---
title: "Can't get 1920x1080 res on HD Panasonic 50PF9U"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by Rizlaw on 2007-06-11
I have a new commercial Panasonic 50PF9U plasma display with a DVI input card (FB9FDD) which is capable of full 1920x1080p resolution. The Panasonic DVI card correctly identifies itself to both the Windows and Ubuntu OS's as "FB9FDD". My dual boot Shuttle (XP Pro and Ubuntu 7.04) has an Nvidia FX5200 card. In WinXP I can set the Nvidia driver to connect and perfectly output 1920x1080p to the Panasonic display in dot by dot mode. In Ubuntu, the best resolution I can get is 1440x1050 using "sudo nvidia-settings." Ubuntu is using the proprietary Nvidia driver and I can configure Xorg to 1920x1200 when connecting to a Samsung SyncMaster 243T with no trouble. The problem is clearly in the Linux Nvidia driver.

I have read a many of the threads in the forum about users who can't get 1920x1080 when connecting to a TV monitor capable of 1920x1080p.  I noticed that the Linux version of the Nvidia driver (unlike the Windows version) does not have an "HDTV" switch setting. I am of the opinion that the lack of this setting in the Linux Nvidia driver is why I can't get 1920x1080p which is a HDTV resolution and not a computer monitor resolution.

Has anyone had any success getting Feisty to work on my hardware, or anything similar?  Thanks.

---

### Post by scott_g on 2007-06-11
I don't have an HD monitor like that, but Feisty used to limit my resolution when I had my screen refresh rate in the xorg.conf file too low.  If you do a gtf res refresh in the terminal (eg: gtf 1920 1080 "refresh rate"), it will tell you what the hsync value should be.

Sorry I can't be of more help,
Scott

---

### Post by imnotryan on 2008-01-06
Edit : wrong thread.

---

