# zWSA — Windows Subsystem for Android (x64) — Public Releases

This repository hosts the **prebuilt zWSA packages** only. You download and
install them here; the build tooling and source stay in the private
`zamarax-windows/zWSA` repository.

zWSA repackages Microsoft's final Windows Subsystem for Android build
(**2407.40000.4.0**, Android 13) with **Google Play (MindTheGapps 13.0)** and
your choice of root manager.

> **Heads up:** Microsoft ended support for WSA on **March 5, 2025**. This
> project continues to work with the final official build, which remains
> installable on Windows 10 22H2+ and Windows 11.

## Download

Pick the root solution you want. Every package includes Google Play.

| Root solution | File | Size | Notes |
|---------------|------|------|-------|
| Magisk        | `zWSA_Setup_x64.exe` / `zWSA_Setup_x64.msi` | small | Installer; prompts you to pick a variant and downloads it. |
| Magisk        | `magisk.zip` | ~900 MB | Standalone archive (systemless root). |
| KernelSU      | `kernelsu.zip` | ~900 MB | Kernel-level root — **no Magisk**, avoids root detection (e.g. Microsoft Authenticator). |
| None          | `none.zip` | ~900 MB | Google Play only, no root. |

### Easiest install

Download `zWSA_Setup_x64.exe` (or the `.msi`), run it, and choose
**Magisk**, **KernelSU**, or **None** when prompted. The installer downloads the
matching package, registers it, and launches WSA. The chosen root manager (Magisk
or KernelSU) is already included in the image and installs automatically on first
boot; Google Play opens for sign-in.

> These releases are **binary-only** — built WSA packages and installers, no
> source code.

### Manual install (from a `.zip`)

1. Download the variant zip you want.
2. Extract it to a folder on an **NTFS** drive.
3. Open **PowerShell as Administrator**, `cd` into the extracted folder, and run:
   ```powershell
   PowerShell -ExecutionPolicy Bypass -File .\install_wsa.ps1 -InstallDir .
   ```

## Requirements

- Windows 11 build 22000.526+ or Windows 10 22H2 (10.0.19045.2311+).
- x64 CPU with virtualization enabled in BIOS/UEFI.
- Windows features **Virtual Machine Platform** and **Windows Hypervisor Platform**.
- At least 10 GB free on an NTFS partition.

The installer enables these optional features for you (a restart is usually
required before WSA boots).

## Root solutions

- **Magisk** — systemless root with the largest module ecosystem. The Magisk
  app is included and installs automatically on first boot.
  > Note: Magisk root is **pre-applied** to the image. Inside the Magisk app,
  > the "Install" (patch boot image) button will report *"unable to detect
  > target image — installation failed"* — this is expected on WSA (there is
  > no boot partition exposed to patch) and is not an error. Root works.
- **KernelSU** — kernel-level root with no Magisk; better for apps that detect
  root (banking apps, Microsoft Authenticator). The KernelSU manager is included
  and installs automatically on first boot.
- **None** — Google Play with no root.

**Not supported on WSA x86_64:** aPatch (ARM64-only) and KernelSU-Next (no
x86_64 GKI kernel is published for this build).

## After installing

Launch **"Windows Subsystem for Android"** from the Start Menu, sign in to the
Play Store, and start using Android apps.

## Legal

zWSA is not affiliated with Microsoft or Google. WSA and related trademarks are
owned by their respective holders. Downloaded WSA binaries are redistributed
archives of Microsoft's public packages.