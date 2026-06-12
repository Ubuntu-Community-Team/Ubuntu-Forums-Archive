---
title: "ATI Radeon HD5470 on ubuntu 12.04"
date: 2012-04-27
forum: Multimedia Software
---

### Post by DaveDeviant on 2012-04-27
Is someone here who succeeded installing ATI Radeon drivers on Ubuntu 12.04 and make them working? If I use the drivers from "additional drivers" actually my system isn't working perfectly (compiz, woobly effect and other effects become automatically disable after a restarting).
Thanks

---

### Post by Senior_Buckethead on 2012-04-27
Hi
I had a problem with my ATI Radeon 3450 fglrx driver not working under 11.10, and 12.04 would be no different. I had to take my graphics card out to make my system run. Is your Radeon a graphics card or on the motherboard? Is it a Desktop Or a laptop?

Have a read of this:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

### Post by QIII on 2012-04-27
Yes, it does work.  I've used the drivers for years and have been using the fglrx driver on Kubuntu and Xubuntu Precise from the start.

I'm standing on a train right now on the way home, but if you haven't gotten a resolution by the time I get home, have dinner, play with the grandkids and finally get on the computer, I'll help you resolve this.

Edit:  I just happened to think of something when the train went in to a tunnel.  Are you using GNOME?

Edit:  Just did a clean install of the fglrx driver on the machine I am currently typing from.

1.  Save backup copy of xorg.conf in case this doesn't work.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```2.  Remove/purge current fglrx and fglrx-amdcccle
```
sudo apt-get remove --purge fglrx*
``````
sudo cp  /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```3. Install lthe driver.
 ```
sudo apt-get install fglrx fglrx-amdcccle
```4.  Generate a fresh xorg.conf
```
sudo aticonfig --initial
```5.  Reboot.

I get all the wiggly eye candy a guy could want.  (But there is a known  problem with GNOME, which the GNOME developers are working on.  It's not  a problem with the driver itself.)

Then, to get full hardware acceleration:

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```I get all the wiggly eye candy a guy could want.  (But there is a known problem with GNOME, which the GNOME developers are working on.  It's not a problem with the driver itself.)

---

### Post by DaveDeviant on 2012-04-28
> **QIII said:**
> Yes, it does work.  I've used the drivers for years and have been using the fglrx driver on Kubuntu and Xubuntu Precise from the start.

I'm standing on a train right now on the way home, but if you haven't gotten a resolution by the time I get home, have dinner, play with the grandkids and finally get on the computer, I'll help you resolve this.

Edit:  I just happened to think of something when the train went in to a tunnel.  Are you using GNOME?

Edit:  Just did a clean install of the fglrx driver on the machine I am currently typing from.

Here's what I did:

1.  Remove/purge current fglrx and fglrx-amdcccle
2.  Save backup copy of xorg.conf in case this doesn't work.
3.  ```
sudo apt-get install fglrx-updates
``` which installed both the driver and the Catalyst Control Center
4.  ```
sudo aticonfig --initial
``` to generate a fresh xorg.conf
5.  Reboot.

I get all the wiggly eye candy a guy could want.  (But there is a known problem with GNOME, which the GNOME developers are working on.  It's not a problem with the driver itself.)

Then, to get full hardware acceleration:

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```

Hi, I'm using unity and I'm a linux user for approx. 1 month. So a detailed instruction of "how to" will be awesome.
Thank you!

---

### Post by bbemmerful on 2012-04-28
Post those cmds in the terminal

---

### Post by DaveDeviant on 2012-04-28
Ok, but first of all I need to install fglrx from additional drivers and than remove it and following those commands?

---

### Post by forbidden404 on 2012-04-28
> **DaveDeviant said:**
> Ok, but first of all I need to install fglrx from additional drivers and than remove it and following those commands?

You said about the fglrx driver that wasn't working.

purge command will uninstall the fglrx and his libs, so this a complete cleaning for you before.

After this you will open the terminal (Ctrl + shift + t) and then you will follow that instructions.

Actually I've NEVER had one day of peace after I tried to use fglrx driver. I have a Intel HD Graphics 3000/AMD Radeon HD5470, same as you, and the first time, I broke Xorg, second time, everything became in 2D mode, so I do not recommend for you to put the proprietary driver.

---

### Post by DaveDeviant on 2012-04-29
> **forbidden404 said:**
> You said about the fglrx driver that wasn't working.

purge command will uninstall the fglrx and his libs, so this a complete cleaning for you before.

After this you will open the terminal (Ctrl + shift + t) and then you will follow that instructions.

Actually I've NEVER had one day of peace after I tried to use fglrx driver. I have a Intel HD Graphics 3000/AMD Radeon HD5470, same as you, and the first time, I broke Xorg, second time, everything became in 2D mode, so I do not recommend for you to put the proprietary driver.

I just followed those commands but it doesn't working. After 5th part, "reboot", a pop-up came out with some options saying "run in low graphic mode" "configure graphic".... and so on. For every of this option the log in screen does not appear.
So, I'll stick to default graphic mode.

---

### Post by forbidden404 on 2012-04-29
> **DaveDeviant said:**
> I just followed those commands but it doesn't working. After 5th part, "reboot", a pop-up came out with some options saying "run in low graphic mode" "configure graphic".... and so on. For every of this option the log in screen does not appear.
So, I'll stick to default graphic mode.

I don't know, so....
Look, in my case, I never could use fglrx, always had problem with it, I don't recommend this for you, just use the open source and wait to AMD do a decent stable driver

```
 
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
  sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Try this to remove completely fglrx and reinstall Xorg

---

### Post by DaveDeviant on 2012-04-29
> **forbidden404 said:**
> I don't know, so....
Look, in my case, I never could use fglrx, always had problem with it, I don't recommend this for you, just use the open source and wait to AMD do a decent stable driver

```
 
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
  sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Try this to remove completely fglrx and reinstall Xorg

I re installed the system ... and as you said, I'll just wait for a stable version IF someday will be :)

Thanks for all the help guys.

forbidden404, if you use a laptop please take a look here - [http://ubuntuforums.org/showthread.php?t=1968660](http://ubuntuforums.org/showthread.php?t=1968660)

---

### Post by Feathers McGraw on 2013-04-07
> **QIII said:**
> 
```
sudo apt-get remove --purge fglrx*
sudo cp  /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo apt-get install fglrx fglrx-amdcccle
sudo aticonfig --initial
```
reboot

Then, to get full hardware acceleration:

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```


This worked perfectly for me, and introduced me to Kubuntu - I didn't even know about KDE before you posted and had been trying loads of different things in GNOME with no success.

Thank you!

---

### Post by Feathers McGraw on 2013-09-22
Just in case it's useful for anyone else stumbling across this thread, I found a different solution with the help of some folks at [Kubuntu Forums]("www.kubuntuforums.net").

The solution mentioned here (in the thread) worked on 12.04 but not on newer versions of Kubuntu. The solution I'm linking to doesn't use any proprietary drivers and works in newer versions of Kubuntu.

I've written it up at the link below, but basically the solution is switching off power to an unused graphics card.

[http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/](http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/)

Hope this is useful to someone.

Feathers

---

