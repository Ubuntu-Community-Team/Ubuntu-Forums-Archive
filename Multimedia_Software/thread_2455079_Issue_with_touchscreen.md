---
title: "Issue with touchscreen"
date: 2020-12-11
forum: Multimedia Software
---

### Post by youpick78 on 2020-12-11
Hi, I'm new here and I recently installed ubuntu but he didn't recognize the touchscreen from my toshiba Satellite U920t. I tried to check the peripheric reference but I didnt thind any thing either with xinput --list and with lsusb. I've also checked if toshiba released driver for touchscreen but I want able to find anyone.
Thanks for your time

---

### Post by CelticWarrior on 2020-12-11
Welcome.

Please check 'lspci' also.

And check the UEFI settings as it may have been disabled there. Other users reported it working without additional drivers: [https://askubuntu.com/questions/329186/ubuntu-on-toshiba-u920t-023](https://askubuntu.com/questions/329186/ubuntu-on-toshiba-u920t-023)

---

### Post by youpick78 on 2020-12-12
First thanx for you awnser.
I tried lspci and it didn't show me anything that can be relative to touchscreen, and I really don't understand that much at the thing that the guy did with Gruub cause I just don't really know how it work.
And for UEFI if I enable it in the BIOS my laptot simply not start, it say that I need to insert system disk.

---

### Post by CelticWarrior on 2020-12-12
UEFI is what replaced BIOS a long time ago. So, strictly speaking and using the correct terminology, if you have UEFI you don't have BIOS. Yes, many vendors still call it "BIOS" or "UEFI BIOS" incorrectly.

So...
> [COLOR=#000000]And for UEFI if I enable it in the BIOS my laptot simply not start, it say that I need to insert system disk.[/COLOR]
This means you installed in Legacy/CSM/"BIOS" mode, a UEFI feature for "emulating" the old BIOS boot process for backward compatibility with OSes that don't support UEFI mode (that would be XP in Windows world; Windows 7 had support for it).

Except in very rare situations, **any UEFI compatible OS should be installed in UEFI mode in UEFI hardware**.
That you have it in Legacy mode may very well be the cause for some hardware to not work.
Again, the link above was just to show you that even in the day, with older Ubuntu releases, users had some issues but NOT with the touchscreen, users commented it "just works" without additional drivers or user settings.

---

### Post by youpick78 on 2020-12-12
okay, and would it be possible to adapt ubuntu to launch it via UEFI and no longer CSM? I don't know if it can help but the file /boot/efi is empty.

---

### Post by CelticWarrior on 2020-12-12
Yes, it's possible but I don't know the details, never done it.

AFAIK, it should work as long as you have or create the ESP (EFI System Partition), a small FAT32 partition typically at the beginning of a drive (but doesn't have to be, I think) and then install the Grub EFI bootloader.

---

### Post by youpick78 on 2020-12-12
Okay I've done it I've totally reinstalled ubuntu in UEFI mode and I want to do this part : "[COLOR=#242729][FONT=Arial]manually change the Windows boot file in /EFI/Boot with the grub one" from the other forum but I don't know where to create the windows boot file and how should I name it cause I have erased [/FONT][/COLOR]entirely my disk so nothing remain from windows.

---

### Post by CelticWarrior on 2020-12-12
If nothings remains from Windows why would you need to be mucking about Windows bootloaders?
And each OS installation creates its own and saves it in the ESP. Thanks to the UEFI boot specifications bootloaders co-exist now, Grub won't replace the Windows bootloader, users select which one to boot from in the UEFI settings > Boot.

You should familiarize yourself with UEFI because you're ten years late already (in the IBM-PC compatibles universe; UEFI was already the standard in Apple years before it started in PCs).

Does the touchscreen work now?

---

### Post by youpick78 on 2020-12-12
I know that I don't know that much about that part of computer and that's why I ask, but I know that I can't choose the boot (or at least with an obvious way) from my BIOS/UEFI (one option is selecting the alimentation of the BIOS with BIOS written instead of UEFI so I stick to BIOS) menu I've checked every parameter one by one and non of them correspond (the only thing that I can choose is the start order in which are shown only Usb memory one other usb parameter and my SSD. 
The reason why I asked you where do I need to place Gruub is that I think that due to the lack of boot choice or option to select an Efi as thrusted (this option is missing even when I add a password to my BIOS) the system seems to be created in a way that he will seek at each start at the exact same location for the thrusted Efi source)

---

### Post by CelticWarrior on 2020-12-12
A cursory search about your computer + Ubuntu reveals nothing suggesting it needs workaround and/or obscure UEFI settings changed. That said it's also one of those from the very beginning of mandatory UEFI installations for Windows (~2012 with Windows 8) and some firmware of that vintage do indeed cause problems when installing in the proper mode. However, the same search shows that users have been installing Ubuntu in UEFI mode in that computer since then and reporting no issues.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) (this has been around for a very long time already).
No understanding this is NOT an option if you're installing/managing OSes nowadays and/or troubleshooting hardware.

---

### Post by youpick78 on 2020-12-22
Okay so after a lot of work on this computer I managed to make it show grub at launch (cause before it didn't show it I only had an error like no booting order something like that) so I managed to repair this and the solution to my problem seems to be a bios/uefi update that my computer didn't do before the P0085v170_ECB0v110 bios update from Toshiba (I found I don't remember where but it fixed the problem for some person) So I managed to install win10 thing that I could do before cause the installation software couldn't find any boot order to... But now that win10 is installed I've downloaded the BIOS update wich is a .exe and when I start it it say this : "an error occurred while preparing the update environment. You have not given permission to execute the update." And I don't know what this pression is (I tried the compatibility mode with win8 but didn't work (I will maybe try to reinstall windows but this with 8 instead of 10) and I also tried to start it as an administrator).

---

### Post by CelticWarrior on 2020-12-22
Right-click > run as admin... Or make sure to click yes in the authorization dialog.
Windows isn't that hard.

---

### Post by youpick78 on 2020-12-23
I've done both several time I'm not completely lost on the use of computer.

---

### Post by youpick78 on 2020-12-23
So I've managed to update the BIOS but it didn't do anything and the touchscreen seems to be a relatively common error on the U920t. On the Toshiba website there is no driver for touchscreen and the touchscreen isn't displayed in the device menu even after refreshing it and showing hided devices.

---

### Post by CelticWarrior on 2020-12-23
Have you tested the touchscreen in Windows?

---

### Post by youpick78 on 2020-12-23
Yep didn't work. The touchscreen worked well when it was on windows 8.1 and when I upgraded it to win10 I never managed to get the touchscreen working again the driver may be downloaded from some windows update but I have 137 of them to do and my computer just crash with that many so I don't really what can I do appart from retry installing update

---

### Post by CelticWarrior on 2020-12-24
Or maybe it stopped working and the Windows upgrade was a coincidence.
Or maybe it is disabled in UEFI.

---

### Post by youpick78 on 2020-12-24
I don't think it's a coincidence but it could be and after browsing the UEFI several times I haven't seen any thing that could be related to touchscreen do I any idea of what could it be?

---

### Post by youpick78 on 2020-12-24
And I forgot to add that the touchscreen isn't working in uefi to

---

