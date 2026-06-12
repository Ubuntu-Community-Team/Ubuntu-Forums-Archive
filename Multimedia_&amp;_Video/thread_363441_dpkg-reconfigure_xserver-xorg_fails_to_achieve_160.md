---
title: "dpkg-reconfigure xserver-xorg fails to achieve 1600x1200 resolution"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by rlglende on 2007-02-16
Ubuntu 6.10 AMD64 freshly installed (OK, I have been trying to make this happen for some hours) on a mainboard with the NVIDIA nForce ?4? chipset, GeForce 6600.

No special choices in "dpkg-reconfigure xserver-xorg".  I had to edit it to remove a mistake, but the "/etc/X11/xorg.conf" file is attached.

"/var/log/Xorg.log.0"

There is an error "failed to initialize GLX extension (Compatible NVIDIA driver not found).

This says that it refuses to use the 1600x1200 mode because it exceeds the panel dimensions.

This monitor, at least, comes alive as 'digital'.  My Viewsonic 2030B said 'analog', but otherwise has the same problem.

All this before I make Xinerama work for 2 Samsungs or 2 ViewSonics.

Thanks in advance, I will post the solution.

Please don't flame me for the following Meta Comment:

All this is much too hard.  20 minutes to install Ubuntu, 2 days to get dual-screen working at proper resolution.  2 days EVERY NEW VERSION OF ANY DISTRIBUTION, and the problems are different every time.  No matter how much more sophisticated I get about all these problems, the complexity of X11 and cards, cables, monitors keeps ahead of me.

Ditto for sound.  It broke after the first dist-upgrade after 6.06, doesn't work "out of the box" for 6.10.

I have been using Linux as my home system for 4 years, develop at work on Linux, have used it in embedded systems.  Not a genius at sysadmin, but way more competent than the average user.

My strong impression is that Linux is moving further from a standard desktop, not closer to it.

Lew

---

### Post by rlglende on 2007-02-16
Sorry, these are the attached files 8).

---

### Post by rlglende on 2007-02-16
OK, I see that the file needs a standard extension.

Now we try it.

Lew

---

### Post by kerry_s on 2007-02-16
Your using the open source drivers(nv). Install the real drivers in synaptic or with apt-get(sudo apt-get install nvidia-glx) then change your driver in xorg.conf(sudo gedit /etc/X11/xorg.conf) 	
Driver		"nv"    
to
Driver		"nvidia"   
close and save then reboot. 
Also get rid of-> #	Option		"UseFBDev"		"true"   
You don't need that line. The rest should work fine.

---

### Post by rlglende on 2007-02-17
"nvidia" as the driver, after installing nvidia-glx, works fine.

Thank you so much.

Lew

---

