---
title: "Boot repair not recognize Windows 10"
date: 2019-02-23
forum: MINT
---

### Post by minotavrs on 2019-02-23
Boot  repair error at fix... 

I have Linux Mint 19.1 and Windows 10
Unfortunately grub  not recognize  Windows 10 at grub menu.. 
Windows 10 working standalone only if i type from advanced options of repair the following commands
bootrec /fixmbr
bootrec /fixboot

This is my pastebin info

I have try to manually insert windows 10 at grub but nothing happens

Any help please ?

[http://paste.ubuntu.com/p/GRKxRQJYD7/](http://paste.ubuntu.com/p/GRKxRQJYD7/)

---

### Post by howefield on 2019-02-23
Thread moved to the "*MINT*" forum.

---

### Post by oldfred on 2019-02-23
It looks like you already ran the Boot-Repair autofix which installs grub to the MBR of every drive. With multiple drives that often is not the best choice. But does make it that Ubuntu boots no matter what drive you select in UEFI/BIOS to boot from.

You have the old BIOS/MBR configuration and all drives have the now 35 year old MBR partitioning. Windows in BIOS boot mode required MBR.
But grub can boot from newer gpt with BIOS or UEFI and both Windows & Ubuntu can read gpt partitioned drives.

Windows 10 is not dual boot friendly. I might keep grub in MBR of one of your non-Windows drives and put the Windows boot loader in the Windows drive, sda.
Grub only boots working Windows, or Windows that is not hibernated, nor needs chkdsk. And Windows fast start up turns on the hibernated flag and updates may turn it on again. Then you have to either directly boot Windows or use your Windows repair flash drive or installer with repair console.

You need to install a Windows boot loader to the MBR of sda, to directly boot Windows. Probably your Windows repair disk and fixMBR command.
Not sure if Boot-Repair's advanced mode and selecting sda1 will offer to install a generic boot loader (syslinux) to MBR of sda. You also can from Ubuntu manually install syslinux boot loader, but do not want the full install, just the boot loader part that goes into MBR.

       sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 

If you set UEFI/BIOS to boot sda, then Windows should boot, but may need f8 for repair console.
And if in BIOS you boot sdb or sdc, you should be able to boot Ubuntu. Your Ubuntu probably has an internal setting for major updates to reinstall to sda which you may want to update.

---

