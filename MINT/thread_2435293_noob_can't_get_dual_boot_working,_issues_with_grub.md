---
title: "noob can't get dual boot working, issues with grub-efi-amd64-signed"
date: 2020-01-18
forum: MINT
---

### Post by voidturbulence on 2020-01-18
Hi,

New to Linux and thank you for checking this out.

I'm trying to dual boot Windows 10 and Linux Mint on my Asus UX580.

I downloaded linuxmint-19.3-cinnamon-64bit from the Linux Mint site.
Created Live USB with Rufus on Sandisk Cruzer Fit 8GB, using GPT.
I double checked my System Information on Windows and Bios Mode reads 'UEFI'.

I boot into Live USB from UEFI Boot Menu 'UEFI: Sandisk Cruzer Fit'.
Linux Mint splash appears. If I just press enter (on the first menu option, "try it normally or w.e it was"), it doesn't work and gives a bunch of errors.
So after Googling, I discovered I had to type 'acpi=off' before 'quiet script', after pressing 'e' on that first menu option. Then it worked.

I'm now at the LM desktop so I press desktop shortcut to install. As I go through the install wizard, when it reaches 'installing grub2' it hits me with 'GRUB installation failed.'

I googled a lot:
Disabling/restoring internet connection didn't work.
Tried many things like creating a second EFI partition (first one already made by Windows), didn't work.
Disabling VT-x in my bios, didn't work.
Changing Legacy USB support to Disabled in my bios, didn't work.
Tried splash screen OEM install, didn't work.

Upon opening /var/log/syslog I found this:

```

mint@mint:~$ grep "grub-efi-amd64-signed" /var/log/syslog
Jan 19 02:26:31 mint ubiquity:   grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
Jan 19 02:26:34 mint ubiquity: Get:5 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub-efi-amd64-signed amd64 1.93.15+2.02-2ubuntu8.14 [299 kB]
Jan 19 02:26:35 mint ubiquity: Selecting previously unselected package grub-efi-amd64-signed.
Jan 19 02:26:35 mint ubiquity: Preparing to unpack .../grub-efi-amd64-signed_1.93.15+2.02-2ubuntu8.14_amd64.deb ...
Jan 19 02:26:35 mint ubiquity: Unpacking grub-efi-amd64-signed (1.93.15+2.02-2ubuntu8.14) ...
Jan 19 02:26:38 mint ubiquity: Setting up grub-efi-amd64-signed (1.93.15+2.02-2ubuntu8.14) ...
Jan 19 02:26:39 mint ubiquity: dpkg: error processing package grub-efi-amd64-signed (--configure):
Jan 19 02:26:39 mint ubiquity:  installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Jan 19 02:26:39 mint ubiquity:  grub-efi-amd64-signed
Jan 19 02:26:40 mint ubiquity: Setting up grub-efi-amd64-signed (1.93.15+2.02-2ubuntu8.14) ...
Jan 19 02:26:41 mint ubiquity: dpkg: error processing package grub-efi-amd64-signed (--configure):
Jan 19 02:26:41 mint ubiquity:  installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Jan 19 02:26:41 mint ubiquity:  shim-signed depends on grub-efi-amd64-signed; however:
Jan 19 02:26:41 mint ubiquity:   Package grub-efi-amd64-signed is not configured yet.
Jan 19 02:26:41 mint ubiquity:  grub-efi-amd64-signed
Jan 19 02:26:41 mint grub-installer: info: Calling 'apt-install grub-efi-amd64-signed' failed

```

Appreciate any and all help.

---

### Post by oldfred on 2020-01-18
Mint is not an offical flavor of Ubuntu. Moved to MINT sub-forum.

If you partitioned in advance or manually, you must an an ESP or if installing to any drive other than first drive, first drive must have an ESP for grub to install.
I think Mint uses Ubuntu's Ubiquity installer, which is the problem on where grub gets installed. You can manually install grub to ESP on any drive after install or use Boot-Repair's advanced mode to choose install and drive. But must have ESP for UEFI boot.

Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

