---
title: "Video Drivers for Dell Inspiron 1100"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Leadfinger on 2008-05-01
I have a Dell Inspiron 1100 running 8.04.  The on-board video controller is an Intel 845GM chipset.  Web sites and some pictures look...funny.  So I started checking out my video settings.

When I go to System -> Preferences -> Screen Resolution my "Resolution" and "Refresh Rate" and "Rotation" entries are all blank and un-adjustable.

I tried to download a driver form Intel, but thier site says that if you're running anything older than ~945 chipset that my distrobution should have proper drivers.

Is there a way I can force 8.04 to "re-load" the driver, or something?

---

### Post by PauGNU on 2008-05-01
Try this:

First download packages that you'll need:
```
sudo aptitude install xserver-xorg-video-intel 915resolution
```

Then, edit the file 915resolution:
```
sudo gedit /etc/default/915resolution
```

And add this lines where "XRESO" and "YRESO" are resolution you need (the example is for 1280x800):
```
mode=3c
XRESO=1280
YRESO=800
BIT=32
```

Reboot and... I hope you'll be lucky!

---

### Post by sm0kinace on 2010-08-13
Wonder how this worked out... I'm trying to run lucid on an 1100 with integrated graphics, the display will stay on through boot, but only once every 6 or 7 cycles it will actually stay on at the logon screen. Guess I'll try it and report the next time i can see what i'm doin!

---

### Post by dwpbike on 2010-09-11
bump.  me, too.  kinda fearful of testing these waters.  last try ended up with reinstall of 9.0.

---

### Post by dwpbike on 2010-09-11
gave it a try.  not what i expected.

linda@linda-laptop:~$ sudo aptitude install xserver-xorg-video-intel 915resolution
[sudo] password for linda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No candidate version found for 915resolution
No candidate version found for 915resolution
The following packages will be REMOVED:
  gstreamer0.10-ffmpeg{u} gstreamer0.10-plugins-ugly{u} liba52-0.7.4{u} 
  libavcodec52{u} libavformat52{u} libavutil49{u} libdvdnav4{u} 
  libdvdread4{u} libgsm1{u} libid3tag0{u} libmad0{u} libmpeg2-4{u} 
  libpostproc51{u} libschroedinger-1.0-0{u} libsidplay1{u} 
  libswfdec-0.8-0{u} libswscale0{u} libtwolame0{u} 
  linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 0 newly installed, 20 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 101MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

---

