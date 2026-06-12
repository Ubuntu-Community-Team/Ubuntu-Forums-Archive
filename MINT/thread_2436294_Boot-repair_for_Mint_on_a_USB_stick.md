---
title: "Boot-repair for Mint on a USB stick?"
date: 2020-02-03
forum: MINT
---

### Post by haoleboy2 on 2020-02-03
Aloha. Hope I have the correct forum, if not please let me know.

I have a USB stick onto which I did a full install of Mint 19.1. It worked for a while, and then suddenly stopped working. When I try to boot from it, the machine acts like there is not a bootable partition on the stick.  I've looked at Boot-Repair, but I don't know what advanced options I might need to repair just the USB stick and not the Mint desktop that I'm running Boot-Repair from.  I've generated a boot info report:

[http://paste.ubuntu.com/p/ThpySwQN7C/](http://paste.ubuntu.com/p/ThpySwQN7C/)

The USB stick is /dev/sdd. /dev/sda is an external USB drive, /dev/sdb is the Mint desktop system, /dev/sdc is Windows 10

Any help would be appreciated.

Mahalo,

Harry Z

---

### Post by wildmanne39 on 2020-02-03
*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by oldfred on 2020-02-04
You do not have a bootable partition on the stick.

Do not know Mint, but if like Ubuntu the installer puts grub into the first drive's ESP usually sda or first NVMe drive.
So you can boot full install on flash drive only from internal drive.

Better to have an ESP - efi system partition as FAT32 with boot flag and UEFI boot files in that ESP.
External drives only boot from ESP & /EFI/boot/bootx64.efi. But if bootx64.efi is a copy of the full version of grub, it also need /EFI/ubuntu (does Mint use ubuntu?) for rest of grub's boot files. The installer has a limited grub that only needs a few files to boot installer.

If Mint is using the broken Ubuntu's Ubiquity installer, there is this work around. Bug report is very old. I have installed Debian & Fedora just to see how grub works and both installed correctly to my sdb drive when I selected it. So it only is Ubuntu that does not give a user a choice.

Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

Or you can copy /EFI/Boot & /EFI/ubuntu folders from ESP on internal drive to flash drive. Issue may be another full install overwrote /EFI/ubuntu/grub.cfg which is a 3 line configfile to load the full grub in your install. You may need to check that.
Line 208 in your report shows the UUID of your install in sdb2, so that is your default full grub.
You need a similar entry in the ESP on your flash drive with UUID of your install on the flash drive.

I also use configfile to boot other installs & load full grub menu of that install rather than direct boot of kernel that os-prober adds to grub menu.
Use labels and configfile to boot another install
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359) &
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)

---

### Post by haoleboy2 on 2020-02-04
OK. I will just reinstall Mint on the USB stick. Seems like the path of least resistance.

Mahalo for your reply.

Harry Z

---

### Post by CelticWarrior on 2020-02-04
> **haoleboy2 said:**
> OK. I will just reinstall Mint on the USB stick. Seems like the path of least resistance.

Yes, indeed.

The problem with installations running from USB sticks (or even disks) is that they have a much higher tendency to become corrupted. But keep in mind that when that happens Boot Repair won't help you. It's important to understand its purpose and not be misled by its name. Its purpose is to install/reinstall/manage boot loaders and some firmware settings related to the boot process. A system that is booting already doesn't need Boot Repair as if later it doesn't than Boot Repair won't be of any use either, unless the problem is a a user action that resulted in deleting boot loaders.

---

### Post by haoleboy2 on 2020-02-05
> **CelticWarrior said:**
>  ... Its purpose is to install/reinstall/manage boot loaders and some firmware settings related to the boot process. 

This is why I was trying to use Boot-Repair

Harry Z

---

