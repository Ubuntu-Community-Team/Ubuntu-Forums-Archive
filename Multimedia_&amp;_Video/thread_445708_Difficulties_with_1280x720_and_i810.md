---
title: "Difficulties with 1280x720 and i810"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by Funkdafied on 2007-05-16
I've got an Abit iL-90MV motherboard.. it has an Intel 945GT chipset and GMA 950 graphics.

I'm having great difficulty trying to get Ubuntu 7.04 to output a 720p (1280x720) resolution to my Plasma display. I've edited the xorg.conf file to include the resolution but it has no effect.

It seems like other people have been having problems also:
[http://ubuntuforums.org/showthread.php?t=188612](http://ubuntuforums.org/showthread.php?t=188612)
[http://www.linuxquestions.org/questions/showthread.php?t=468094](http://www.linuxquestions.org/questions/showthread.php?t=468094)

But according to the guide below, it is possible to get it to work:
[http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu](http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu)

That last guide says to use a package called "xserver-xorg-video-i810-modesetting".. but when I try to apt-get it, it says its no longer used or something.. and has been replaced by "xserver-xorg-video-intel". I got the latter package but I still couldnt get 720p output. I also tried 915resolution but that didnt work either.

How can I fix the prob?? Any help is greatly appreciated.

---

### Post by veloce on 2007-05-18
> **Funkdafied said:**
> I've got an Abit iL-90MV motherboard.. it has an Intel 945GT chipset and GMA 950 graphics.

I'm having great difficulty trying to get Ubuntu 7.04 to output a 720p (1280x720) resolution to my Plasma display. I've edited the xorg.conf file to include the resolution but it has no effect.

It seems like other people have been having problems also:
[http://ubuntuforums.org/showthread.php?t=188612](http://ubuntuforums.org/showthread.php?t=188612)
[http://www.linuxquestions.org/questions/showthread.php?t=468094](http://www.linuxquestions.org/questions/showthread.php?t=468094)

But according to the guide below, it is possible to get it to work:
[http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu](http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu)

That last guide says to use a package called "xserver-xorg-video-i810-modesetting".. but when I try to apt-get it, it says its no longer used or something.. and has been replaced by "xserver-xorg-video-intel". I got the latter package but I still couldnt get 720p output. I also tried 915resolution but that didnt work either.

How can I fix the prob?? Any help is greatly appreciated.

If you still have 915resolution installed, can you post the output of:

```
sudo /etc/sbin/915resolution -l
```

---

### Post by vikramsharma on 2007-05-18
> **Funkdafied said:**
> I've got an Abit iL-90MV motherboard.. it has an Intel 945GT chipset and GMA 950 graphics.

I'm having great difficulty trying to get Ubuntu 7.04 to output a 720p (1280x720) resolution to my Plasma display. I've edited the xorg.conf file to include the resolution but it has no effect.

It seems like other people have been having problems also:
[http://ubuntuforums.org/showthread.php?t=188612](http://ubuntuforums.org/showthread.php?t=188612)
[http://www.linuxquestions.org/questions/showthread.php?t=468094](http://www.linuxquestions.org/questions/showthread.php?t=468094)

But according to the guide below, it is possible to get it to work:
[http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu](http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu)

That last guide says to use a package called "xserver-xorg-video-i810-modesetting".. but when I try to apt-get it, it says its no longer used or something.. and has been replaced by "xserver-xorg-video-intel". I got the latter package but I still couldnt get 720p output. I also tried 915resolution but that didnt work either.

How can I fix the prob?? Any help is greatly appreciated.

My query might sound trivial, but have you installed the driver for Intel 945.  In case you can use Synaptic Package Manager to install "915resolution", this should solve the problem.

---

### Post by psyke83 on 2007-05-18
> **Funkdafied said:**
> How can I fix the prob?? Any help is greatly appreciated.

By coincidence, today I built a package from the latest source of xserver-xorg-video-intel (which uses modesetting), I'll attach it to this post.

I'm not sure if you need Xorg 7.3, let me know if you've problems.

To install (with deb in current path):```

sudo apt-get remove xserver-xorg-video-i810; sudo dpkg -i xserver-xorg-video-intel_2:2.0.0-1conn2-1_i386.deb
```

To uninstall: 
```
sudo apt-get remove xserver-xorg-video-intel; sudo apt-get install xserver-xorg-video-i810
```

---

### Post by Funkdafied on 2007-05-18
Thanks for the responses all.

**veloce**: When I run 915resolution I get the following...
```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

I have tried replacing 5c with my desired res (# 915resolution 5c 1280 720) but after a reboot it resets itself back to the above. 

**vikramsharma**: I believe Ubuntu should already have the correct drivers for my motherboard ([source]("http://www.intellinuxgraphics.org/download.html")). As above, 915resolution didn't do much for me.

**psyke83**: Thanks for the file.. Seems quite promising. I'll try it out and report back.

---

### Post by Funkdafied on 2007-05-18
**psyke83**: What should I put as my Device->Driver in xorg.conf? It's currently set to "i810" but that no longer works with the package you uploaded.. "intel" doesn't seem to work either.

---

### Post by Funkdafied on 2007-05-18
I checked the readme and my driver should be set to "intel" but it still fails to load. I get the following in my xorg.0.log:

```
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
dlopen: /usr/lib/xorg/modules/drivers//intel_drv.so: undefined symbol: xf86CrtcConfigPrivateIndex
(EE) Failed to load /usr/lib/xorg/modules/drivers//intel_drv.so
(II) UnloadModule: "intel"
(EE) Failed to load module "intel" (loader failed, 7)
```

Any ideas?

---

### Post by psyke83 on 2007-05-18
Funkdafied,

That driver was built for Xorg 7.3. You can *try* adding a repository but I don't guarantee it'll work (it's not mine). Edit /etc/apt/sources.list and add to the end:

```
## Xorg 7.3
deb http://www.burtonini.com/debian/ feisty/
deb-src http://www.burtonini.com/debian/ feisty/
```

Then run:

```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo apt-get install xserver-xorg-video-intel
```

This repository contains the core xserver 7.3 packages and the 2.0.0 intel modesetting driver.

If that doesn't work, temporarily go back to the vesa driver and/or downgrade these packages.

P.S. The new modesetting driver will accept the driver name "intel" and "i810" alike, but the old 1.7.4 driver only accepts "i810", so leave that in your xorg.conf.

---

### Post by psyke83 on 2007-05-18
Funkdafied,

Some further thoughts: are you sure you set up 915resolution correctly? My laptop has a bog-standard 1024x768 panel and so I've never had a use for it, but if I recall correctly I believe 915resolution may need to be set as a startup script, because it soft-mods the BIOS (i.e. patches the functions in memory) which don't survive a reset.

Instead of using the new (unstable) packages I mentioned above, you may want to do some more research on 915resolution instead.

EDIT: Instructions are available in /usr/share/doc/915resolution/README.Debian

---

### Post by veloce on 2007-05-18
> **Funkdafied said:**
> Thanks for the responses all.

**veloce**: When I run 915resolution I get the following...
I have tried replacing 5c with my desired res (# 915resolution 5c 1280 720) but after a reboot it resets itself back to the above. 



You need to set the resolution with 915resolution manually.  To do this you need to edit the 915resolution config file:

```
gksudo gedit /etc/default/915resolution 
```

You can leave "mode = auto" just uncomment and complete the xres= and yres= lines.

These changes are kept between reboots.

---

### Post by Funkdafied on 2007-05-19
> **veloce said:**
> You need to set the resolution with 915resolution manually.  To do this you need to edit the 915resolution config fileyay.. this finally got it working!

still got a problem though.. I'm using MythTV on this box.. and while the UI and everything works fine, when I go to play videos or watch TV it just shows a blank blue screen. I didn't have this problem before the resolution change.. and it doesn't happen when I run mplayer directly. Not sure what it could be :confused:

---

### Post by cantormath on 2007-06-07
Buy an Nvidia Card for a couple bucks and never worry about this ever again......

---

### Post by Funkdafied on 2007-06-07
nVidia don't have a solution that meets my needs.

---

### Post by cantormath on 2007-06-08
> **Funkdafied said:**
> nVidia don't have a solution that meets my needs.

What are you needs exactly?

---

