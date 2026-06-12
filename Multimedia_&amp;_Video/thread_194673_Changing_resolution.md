---
title: "Changing resolution"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by bleakcabal on 2006-06-11
Hi. When I upgraded to Dapper it changed my XORG conf file and changed my resolution form 1024 to 1280. I don't like this new resolution since I have a small screen. 

I opened and modified /etc/X11/xorg.conf with sudo privileges and erased all mentions of 1280x1024 in the file. The first entry is now 1024.

I restarted my X session but the resolution does not seem to have changed...

---

### Post by CujoQuarrel on 2006-06-11
Same here. Trying to go from a higher res to a lower res but even after removign all mentions of the higher res from the xorg.conf I still get that resolution. 

Where is it getting it's information from?

CujoQuarrel

---

### Post by asc on 2006-06-12
If you're editing text files, you should know how to view system logs. What does the X.org log file tell you?

You can also try using the Gnome resolution switcher under System->Preferences->Screen Resolution

---

### Post by ianmac on 2006-06-15
I can edit text files, but after being away from linux for a while, I'm not sure where the system logs are...  can you help me out?  I tried to change the system resolution as well, but nothing seems to happen.  I changed my xorg.conf file, and took out all 24 bit modes, but now all I can get is 16 bit, 1600x1200 mode, which besides making things too small for even my reasonably ok vision, it eats up a lot of processor cycles, which are unnecessary.  If I do an Alt-Ctrl-+ and -, the screen resolution changes, but the desktop size does not, which isn't what I'm after either.

What are the important log files to be generally looking at?  I can dmesg, but that is more hardware, correct?  I was trying to setup my modem, but was mystified when pon seemed to dial up, but nothing seems to happen...  maybe I'll have to do a search for log file locations...

Ian

---

### Post by jis on 2006-09-18
Maybe Asc ment /var/log/Xorg.0.log ? Maybe you could try to set vesa driver in xorg.conf Device section?

I wonder how Xubuntu remembers the resolution used in the last session before restart? How could I change resolution, if I am using Xinerama? (In Xubuntu you can normally change the display&desktop resolution in the Settings > Display Settings dialog, but this is disabled, when Xinerama is enabled.)  I have noticed that changing even the order of resolutions listed in xorg.conf may have undesired effects, but it is needed to change the first item to be able to change the login screen resolution (See [this]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-9a8fa8e79e2458de1eb69eadb2c97a633be81a42")). 
Nowdays the Mice2 Splash Engine (Xubuntu splasch screen) is not running in the center of my (primary) screen.

---

