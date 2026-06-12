---
title: "Using Boot-Repair to repair bootstrap in Mint"
date: 2024-09-24
forum: MINT
---

### Post by jimy123 on 2024-09-24
Hi All
I am new to Mint and my main operating disk sda (300GB) ceased to boot unless booted from another disk sdb (4TB) that gives a choice of disks to boot from.
Am trying to use Boot-Repair but need advice before doing so in case I make it worse.
The Boot-repair summary is at [COLOR=#000000]https://paste.ubuntu.com/p/mDxNMdgdpt/ but is meaningless to me.
My computer is 14 years old and uses BIOS.
[/COLOR][COLOR=#000000]Any advice on what to do next would be greatly appreciated.
Jim



[/COLOR]

---

### Post by coffeecat on 2024-09-24
Not Ubuntu. *Thread moved to the **MINT** sub-forum.*

---

### Post by yancek on 2024-09-24
If you can boot Mint and LMDE from the Mint drive, what's the problem?  If you want to boot LMDE on the smaller disk, what happens when you set  that drive to first boot priority in the BIOS?  It should boot LMDE first and if you run sudo update-grub from LMDE, you should see Mint added to the Grub menu.   Your LMDE drive has Grub in the MBR and should if set to first boot priority, boot LMDE.  

Have you gone into the BIOS firmware and verified there are no options for UEFI?  I see in boot repair (line 154) shows sdb2 as an EFI partition which would be useless if you can't boot EFI.   On the Mint drive, sdb1 shows as a BIOS_boot partition which is needed on a GPT drive (which sdb is) to boot a Legacy install of Linux with Grub.

If you want to boot with LMDE, you can  boot it from the second (Mint) drive and run sudo update-grub  from LMDE and then set that drive to first boot priority.  I'd do that before anything else.

---

### Post by oldfred on 2024-09-24
You show sda as BIOS/MBR and sdb as UEFI/gpt.
You do have bios_grub for BIOS boot and an ESP - efi system partition for UEFI boot on sdb.
You can easily convert an UEFI install to BIOS boot just by reinstalling correct version of grub.
Grub uses grub-pc for BIOS boot and grub-efi-amd64 for UEFI boot.

Your install on sdb is currently UEFI as you have boot files shown in ESP and mount of ESP in fstab see lines 340, 341.

How you boot install media on USB flash drive UEFI or BIOS is both how it installs & how it repairs.
Grub can only boot other installs in same boot mode, or both must be UEFI or both BIOS.

You probably can boot sda from BIOS from UEFI/BIOS one time boot screen, but may have to change UEFI settings to default boot in BIOS and change back to boot in UEFI mode to boot sdb. Some systems recognize boot mode of selection & auto switch.

If UEFI booting working ok, then long term better to plan to convert sda to UEFI/gpt.
But conversion from MBR(msdos) to gpt totally erases drive, so good backups required.

---

### Post by jimy123 on 2024-09-24
Thank you both for your replies.
This is a bit too technical for me, so I will wait until I get a new computer in a few months that will only have UEFI and so may be easier to fix the Grub.

---

