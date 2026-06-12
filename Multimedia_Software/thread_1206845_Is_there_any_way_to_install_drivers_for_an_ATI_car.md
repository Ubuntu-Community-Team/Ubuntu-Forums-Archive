---
title: "Is there any way to install drivers for an ATI card?"
date: 2009-07-07
forum: Multimedia Software
---

### Post by litlfrog on 2009-07-07
My Linux hatred is really building up today. I've been trying to get working video drivers installed for hours. I tinkered with the onboard NVIDIA video for a while before giving up and slapping a Radeon 9000 video card in the AGP slot. When I go to System -> Administration -> Hardware Drivers, it doesn't list any proprietary drivers. The ATI page has drivers for the card, but I can't get either one to install. There's a file that ends with a .run extension; when I tried to run 

> sh ./ati-driver-installer-8.28.8.run

it started to uncompress the package, but then showed

> Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install


So I tried the other one, a file ending in .rpm. When I double-click that, I just get "Archive type not supported." Seriously, it shouldn't be this hard to install a video card; does anyone have a simple way to do this?

---

### Post by Metaljaz on 2009-07-07
For Jaunty:

[http://ubuntuguide.org](http://ubuntuguide.org)

Scroll down to installing Nvidia / ATI drivers

---

### Post by LepeKaname on 2009-07-07
If that doesn't work, check this thread:

[http://ubuntuforums.org/showthread.php?t=1137467](http://ubuntuforums.org/showthread.php?t=1137467)

it worked for me, however I have a ATI Radeon Xpress 200.

---

### Post by litlfrog on 2009-07-09
Closing to start a new thread

---

### Post by libra1780 on 2009-07-09
thats the moment the driver should start working.
to get something..
-Switch to console (hit alt+ctrl+f1) and after entering as root change the driver in xorg.conf to vesa. 
-kill the kdm process ("ps -ef | grep kdm" and then "kill x" where x is the number at the beginning of the line)
-restart kdm (just type kdm, sometimes kdm -nodaemon is needed, don't know why..)

for this older type of cards the gpl-driver is doing very well, even 3d accel is working good. maybe you'll try that one.

---

### Post by grizlo42 on 2009-07-13
give this a whirl: [http://ubuntuforums.org/showthread.php?t=1203437](http://ubuntuforums.org/showthread.php?t=1203437)

---

