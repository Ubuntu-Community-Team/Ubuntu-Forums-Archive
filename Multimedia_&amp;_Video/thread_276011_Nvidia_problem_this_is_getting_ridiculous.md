---
title: "Nvidia problem: this is getting ridiculous"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by Radiera on 2006-10-12
I'm on Edgy right now, but this is irelevant because I have this problem in every distro I've tried (debian, fedora, gentoo). 
First of all, I'm using the vesa driver (which, by the way, in Edgy is a lot worse than Dapper, but at least they're stable) because the nv driver is very unstable, causing X to crash (also a problem in every distro).

So, naturally, I've tried to install the nvidia drivers. I think I've tried every method u can find on the web, but the result was the same: I don't even get to see the logo screen.

As I said above, I've tried method 1,2 from that tutrial, envy script, tried to blacklist agpgart, same problem!
I have an AthlonXP 1700+, mobo Asus A7V600-x, Inno3d 6600 GT AGP, 1 Gb Ram.

One thing is common though, I get these warnings in xorg.0.log: 
WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x0000dba0, 0x00000b84) and other lines similar to this one.

I'm really getting frustrated. I couldn't imagine having so much trouble when I decided to switch to Linux.

---

### Post by wererabbit on 2006-10-12
Have you tried running Automatix?  It automatically installs and configures your nvidia drivers.  You may need to edit xorg.conf to get other resolutions besides 1024x768, but everything else worked great.

---

### Post by PriceChild on 2006-10-12
I would reccomend restoring the earlist backup you have of your xorg.conf or a ```
sudo dpkg-reconfigure xserver-xorg
```before trying the wiki guides again.

---

### Post by tseliot on 2006-10-12
If you have already tried [my guide ]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") and point 4 of the Problems Section, you can ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Radiera on 2006-10-13
I tried to boot with the option irqpoll for kernel, and i get the message "unexpected irq trap at vector 10" all the time.
This is when I'm booting with the interrupt mode ACPI in Bios, with PIC i don't receive this message.

Also, after i ran lspci, i observed that one souncard and my video card share the irq 201.

---

### Post by Radiera on 2006-10-14
All my problems are gone with the release of the 9626 driver. Works flawlessly!

---

