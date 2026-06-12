---
title: "Screen Resolution is stuck at 640x480"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by tholman_ut on 2006-07-20
I installed Ubuntu just today and I'm trying to set up my desktop.  The first thing I want to do is to adjust my screen resolution, it is fixed at 640x480 60Hz, when I try to make changes in the screen resolution tab it doesn't have any other options.  I want to increase to at least 1024x768 so I can fit a decent amount of stuff on my screen.  I'm guessing that I will need to decrease my color bits (form 24 to 16 maybe, that's what I have to do in windows).  Where can I find/set the color bit and/or screen resolution.

Please give me advice in the simplest terms as I'm VERY new to Linux/Ubuntu.

Thanx
:confused: 
:confused: ](*,)

---

### Post by DomH on 2006-07-20
Hello,
I had te same problem a couple of time.

I suggest you check the answer given here :
[http://ubuntuforums.org/showthread.php?t=188542](http://ubuntuforums.org/showthread.php?t=188542)

It work fine with me.

Have a nice day.

---

### Post by tholman_ut on 2006-07-20
OK i'll give it a shot.
Thanx

---

### Post by ahaslam on 2006-07-20
Have a look in your xorg.conf file and amend as necessary. Colour depth is under *Section "Screen"* and the resolutions should follow. The system should choose the highest compatible resolution upon boot. If you want a windows way to do this, type the following at the terminal: **gksudo nautilus** this will bring up a window with root privileges. Navigate to /etc/X11/ and backup xorg.conf before you start. If you want a quick way use **sudo gedit /etc/X11/xorg.conf** 

Tony.

---

### Post by tseliot on 2006-07-20
Try this nice guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by tholman_ut on 2006-07-22
With all the help I got let me tell you what worked.

First I got into the *xorg.conf* (by doing a *sudo nano /etc/X11 xorg.conf*) file and added *Options "DDCMode" under the [I]"Device"* section.  [/I]Then I tried to modify my file by doing *sudo dpkg-reconfigure -phigh xserver-xorg*, but that didn't work.  So I then got back into the *xorg.conf* and added "1280x960" "1152x864" to the front of what was already there "1024x786"..."640x480" (I probabily should have added it to all of the *Depth*(s) but I only added it to my default *Depth* of 16).  After that and a *sudo /etc/init.d stop* and *sudo /etc/init.d start* the resolution started at 1289x960, but I changed it to 1024x786.

Thanx everybody for the help and I hope this response can help someone else.

Thanx
T

---

