---
title: "No Bootable Device - Linux Mint Cinnamon 20.1"
date: 2021-05-10
forum: MINT
---

### Post by canamon on 2021-05-10
Hello, I'm new to the Ubuntu community.

Few months ago I flushed Windows 10 from my Acer Aspire 11 to install Linux Mint Cinnamon 20.1, yeah!! I was excited. I have booting problems ever since : I finally arrived to the acceptable point where I had to press "enter" 3 times in order to get my computer started (first window appearing : "Default Boot Device Missing or Boot Failed. Insert Recovery Media and Hit any key. Then select 'Boot Manager' to choose a new Boot Device or to Boot Recovery Media" - no need to insert any media, simply pressing enter again was getting me to a second window with choices of boot devices, the correct one on top, press enter again and now the system was booting. I tried to find a solution to avoid these 2 steps but got discouraged and I kept it like that for nearly 2 months, until last week when on that second page, the one that lists the booting devices, the correct booting device was mysteriously missing!!!  Impossible to boot. I read hours of treads suggesting different solutions, none of them worked. 

Going to the bios, boot settings, "Select an UEFI file as trusted for executing" - click enter: the list is completely empty ! nothing to chose from. 

I tried the program 'Boot Repair', it didn't work.

Is there a way to get a new UEFI file  or to retrieve the one I lost  without completely reinstalling Linux Mint?  

Thanks so much!

---

### Post by deadflowr on 2021-05-10
*Thread moved to **MINT***

---

### Post by ajgreeny on 2021-05-10
It will probably be much more useful if you run boor- repair again but this time do not run any repair option, simply choose to run the boot-info script and then post back here the pastebin link you are given.

Have you asked this question at the Linuxmint forum; users there may be able to help more.

---

### Post by canamon on 2021-05-11
running the boot-info summary this time : [https://paste2.org/6KMIOt1s](https://paste2.org/6KMIOt1s)

I didn't know ubuntu and Linux had different forums, I will post there in the future, thanks.

---

### Post by ajgreeny on 2021-05-11
It looks as if you installed Mint in BIOS mode but omitted to create the very small 1M biosBOOT  partition needed òn a gpt partitioned disk,

As you have not yet been  able to use this installation it will probably be quickest and easiest to start again but this time choose the option to boot the USB install medium in UEFI mode then allow the installer to continue às default using the whole disk meaning the partitions required will be created by the system itself.

---

### Post by oldfred on 2021-05-11
Your fstab also shows the mount of the ESP from sdb?

Do not know Mint, but Ubuntu's installer wants ESP on first drive and installs to that.
But since ESP in fstab, you should be able to boot Boot-Repair in UEFI mode and just do a full reinstall of grub from its Advanced options menu.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

