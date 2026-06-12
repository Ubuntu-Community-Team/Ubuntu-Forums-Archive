---
title: "Installing mint on a surface go 4 fails to find disks on boot."
date: 2024-10-29
forum: MINT
---

### Post by skye105 on 2024-10-29
I'm trying to install linux mint 22 on my surface go 4, it works fine until it has to properly boot.
It boots from the live usb, it can see every drive, every module works flawlessly. Upon trying to boot from disk however, it can't find the boot drives. In fact, it can't find *any* drive, /dev/ has no disks.
Grub does see them, I'm just so confused, it's been a week.

Secure boot is off, no windows installation is on here, the disk was wiped to 0 a few times. I've ran boot repair successfully, but i have no idea how to solve the locked nvram issue.

Arch doesn't work either, although that's not surprising.

---

### Post by skye105 on 2024-10-29
[https://paste.ubuntu.com/p/Z2rzJbYmMh/](https://paste.ubuntu.com/p/Z2rzJbYmMh/)
this is the boot repair pastebin, if needed

---

### Post by grahammechanical on 2024-10-29
What suggestions have you been offered at the Linux Mint forums?

[https://forums.linuxmint.com/](https://forums.linuxmint.com/)

Regards

---

### Post by coffeecat on 2024-10-29
Not Ubuntu or Ubuntu flavour. *Thread moved to the **Mint** sub-forum.*

---

### Post by yancek on 2024-10-29
>  Upon trying to boot from disk however, it can't find the boot drives. 

Are you able to access the BIOS to set the /dev/sdd to first boot priority?  That is the disk which shows as 119GB.  Line 182 shows it as a GPT drive and you have an EFI partition which shows beginning at line 122.  Line 144 shows Mint on /dev/sdd2 but there is no information on any files on the drive.  I see an efi entry for ubuntu on line 164, Boot0004 which is the Mint entry in all likelihood.  What is Boot0007 which shows as Linux Boot Manager?  What happens when you make each of these selections in the BIOS EFI menu?

---

