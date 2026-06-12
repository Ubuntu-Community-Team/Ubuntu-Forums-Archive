---
title: "Startup screen is 'out of  range' says my monitor"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by Eelke81 on 2007-05-04
Hello dear Ubuntu-friends,

I wonder if any of you can help me with the following problem: I just bought a 'new' videocard, an ATI Radeon 9200SE with 128mb videomemory. I installed it in my computer and I ran the X-reconfiguration utility (dpkg-reconfigure xserver-xorg). The utility detects the right videocard and my Gnome runs excellent with the new card, even with Beryl. So far so good. But when I start the computer and select Ubuntu from GRUB, the graphical startup-screen of Ubuntu isn't displayed, instead my monitor says: Out of Range, 46.4kHz / 87Hz. 

I tried to solve this problem by changing the Horizontal and Vertical refresh rates in the xorg.conf file, according to the values in my monitor's manual. With no result. I even tried adding the vga=-option to the startup command in GRUB's menu.lst file to force the startup screen to be displayed in a different resolution. The result of this is that the startup-screen indeed is displayed in the resolution that matches the vga=-option, only the problem is that the ubuntu logo is not in the middle of the screen, but is 'blown up' in the down-right corner and also that my X/Gnome won't start after the displaying of the startup-screen. Probably because the resolution I use for X/Gnome is different from the vga=-option.

Does anybody have a suggestion how I can solve this problem? 

My computers's specifications:

AMD Athlon XP 2400+ processor
256mb RAM
ATI Radeon 9200SE 128mb
LG Flatron L1917S monitor (maximum resolution: 1280x1024 at 75Hz, however: 60Hz is recommended)
Horizontal  Refresh rate: 30-83 kHz
Vertical Refresh rate: 56-75 Hz
I am using Ubuntu 7.04 with GNOME 2.18 and Beryl, running at the highest recommended resolution possible: 1280x1024 at 60Hz (without any problems with X/Gnome)

Kind regards,



Eelke

---

### Post by Tux Aubrey on 2007-05-04
Sounds like the same problem we sort of resolved in [this thread- Link]("http://ubuntuforums.org/showthread.php?p=2010641").  See if it works for you.

---

### Post by Eelke81 on 2007-05-05
Thanks for your reply. When I try to add the vga option to the commandline in GRUB, all the 1280x1024 resolutions don't work, but when I try a lower resolution, for example: 1024x768, the startup ubuntu picture is displayed but not in the right way: instead of the middle of the screen, it is displayed in the bottom right corner. So my guess is that ubuntu still tries to display the picture for the 1280x1024 resolution on a 1024x768 resolution. Do you or anybody else know how to fix this?

Kind regards,


Eelke

---

### Post by Eelke81 on 2007-05-09
Okay, I solved the problem by using a program called Startup-Manager, which can be found here:

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

With it you can change almost every option in GRUB without having to edit the menu.lst file manually by yourself.

---

