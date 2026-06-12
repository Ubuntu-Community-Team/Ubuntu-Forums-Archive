---
title: "Can't run or install ubuntu from CD onto pavilion ze5700"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by Dangsos on 2009-01-22
I can't seem to do anything with this computer that uses bluetooth wireless, I installed a fresh copy of windows on it and can't seem to get the wireless working.  What I really want is to put linux on it though, and I have no idea where to start.

When I do actually try to put linux on there it flashes some error numbers for a very brief ammount of time that I can't read because it goes up so fast, however I did see that it was telling me to visit [www.linuxwireless.org/en/](www.linuxwireless.org/en/)  so naturally I went there and I'm not sure what I'm looking for.

any help would be appreciated

EDIT:  I also see that this laptop (pavilion ze5700) uses bluetooth technology which I know nothing about the drivers involved in that

---

### Post by Macchi on 2009-01-22
A few comments about your post:
> **Dangsos said:**
> I can't seem to do anything with this computer that uses bluetooth wireless...
Unfortunately there are many ways things can go wrong, specially with Bluetooth. It could be a wrong setup on the BIOS, bug in the BIOS+firmware, wrong steeings in the operating system, wrong settings in the devices, devices that do not follow standards, or in the worst case o hardware problem. See the suggestion below.



> **Dangsos said:**
> ...What I really want is to put linux on it though, and I have no idea where to start...


I would recommend you to download [here]("http://www.ubuntu.com/getubuntu") the latest Ubuntu 8.10, burn it to a CD and boot your computer with it. Then you will have the possibility to run one of the best GNU/Linux distributions available today. 
From the live CD you will be able to run without changes to your computer or to install Linux, with the option of keeping or removing the existing operating system.
Perhaps you know this, but I mention it just in case.

You will be able to test most of your hardware, hopefully also your Bluetooth. Hope it works and keep in touch!

---

### Post by Dangsos on 2009-01-22
It seems I didn't specify enough to get helpful feedback.....I saw something that said I needed new firmware and in parenthesis I recall seeing version 3.0 I believe?  anyways it won't let me run linux from the CD either it gives me the same error

again thanks in advance for any help...I'm fairly stumped on what to do because I can't find hardly any info via google

---

### Post by Macchi on 2009-01-24
Hi Dangsos,


BOOT FROM THE LIVE CD
To run the Ubuntu live CD you have to boot the computer with the CD, but this is NOT default setting on many cases. 
You have four alternatives:

1) Try pressing the key "F8" os 2) "ESC" right after you power on the machine and you should get a menu with options to choose the boot media.

3) Otherwise change the boot order in the BIOS.

4) Additionally Ubuntu you may install from Windows

If you cannot succeed booting then you could try testing the live CD on another computer. Try also the alternative to Check the CD. It is common to see errors on a)downloading and b)burning a disk image and c) mechanical or other problems on the reader regarding specific discs. 


PS: Booting Ubuntu is according to my experience very reliable. Choosing the right settings the success rate is very high. The problems that I run into are often related to hardware problems or very exotic hardware.
I can tell that after the experience of approx 50 Ubuntu installations, out of a total of 150 GNU-Linux installations, both in professional and experimental envinronments. 


Regarding messages on hardware or outdated firmware, you should check if the equipment manufacturer or provider has any important updates for your BIOS.

---

### Post by Dangsos on 2009-01-24
I'm just now able to access the internet with the laptop, so I'm going to run around hp's site and look for some bios upgrades and whatnot and hopefully I'll find something, I'll keep you posted

as for booting from live CD, that's not the problem I assume because I get the exact same error and automatic reboot that I get when trying to install from CD, and there are no problems with the CD, I've used it on this machine that I'm on right now :) and I have of course checked the CD for problems with the CD checking option at menu

---

### Post by Dangsos on 2009-01-24
this is the code that flashes when i try to boot from a live CD or install ubuntu

b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found
or load failed.
b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and
download the correct firmware (version 3).

---

### Post by Dangsos on 2009-01-25
bump

---

### Post by Dangsos on 2009-01-26
for anyone that comes across this thread, I think I resolved the issue, I was unaware that ubuntu's installation required more than 256mb RAM for installation and I'm thinking thats the reason it froze.  I downloaded the less hardware intensive installation version and I am now installing ubuntu 8.10 and will let you know if it works.

---

