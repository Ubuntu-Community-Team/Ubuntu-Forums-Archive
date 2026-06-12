---
title: "Ubuntu with nvidia 7800 GT"
date: 2005-11-10
forum: Multimedia &amp; Video
---

### Post by steelerguy on 2005-11-10
First a little background:
I was a Gentoo user for a couple years and really liked the distro, but hated all the compiling.  I then moved to Arch Linux so I could just get binaries and really liked it also.  I put together a new computer with an AMD64 x2 chip and nvidia Geforce 7800 GT video card.  Arch does not have a 64-bit distro so I figured I would try Ubuntu since I had been hearing lots of good things.

Now my problems:
Other than problems with a USB keyboard through a KVM I had no problems installing Ubuntu. Everything was looking very good until I tried to log in.  Typed username and password and the screen (other than mouse) locked up before Gnome started.  Had to reset, tried to change to failsafe Gnome in gdm and video locked up again before even hitting OK.  Not off to a good start.

I read an nvidia guide on here that assumes you are currently in a window manager, and tells you how to use GUI tools which I could not use.  It did steer me in the correct direction and I got the latest nvidia drivers directly from nvidia.  Compiled and installed them after getting supporting packages mentioned.  Still a no go, it is trying to load the old nvidia driver and will not let me uninstall it.  When I do an insmod on the correct driver it will not load either.  Very frustrating first experience with Ubuntu.

Now I work on Linux machines all day, the last thing I want to do when I come home is have problems with my home machine.  I don't mind putting in a little effort into getting this running, but the number of steps to still have it not work is a bit ridiculous.  Does anyone know when the 7676 drivers from nvidia will be a part of Ubuntu so the 7800 GT will work without jumping through hoops?  Has anyone done a fresh install with a 7800 GT and gotten it working?

I wanted to use Ubuntu for the great package manager, now I find the first thing I am doing is trying to circumvent it which will just cause headaches down the road.

Thanks in advance for the help and putting up with my rant.

---

### Post by bb002 on 2005-11-30
I did a fresh install of Ubuntu with my Nvidia 6800 and got this problem too.

here's what I did to fix it and hopefully it works for you too.

Boot the computer like normal. When you get to the log in prompt at GDM do not login in. Instead press alt+ctrl+f1. This will take you to a terminal.

next type "sudo apt-get install nvidia-glx" without the quotes. and say yes if apt-get askes to install extra packages. also if you are asked for a password type your password in.

once it is installed type "sudo nvidia-settings enable" if that doesn't work try "sudo nvidia-glx-settings enable". If neither work you'll have to edit the xorg.conf by hand.

type "nano -w /etc/X11/xorg.conf"
scroll down through the file until you find a section about nvidia. change the line ```
Driver		"nv"
```
to
```
Driver		"nvidia"
```
now press ctrl+o then press enter to save the file. press ctrl+x to exit.
All that's left is to restart the xserver.
typing "sudo /etc/init.d/gdm restart" will do it. to get back to the GDM screen (if restarting the last command didn't do it press "alt+ctrl+f7".

Now you should be all set.

---

### Post by nothreat33 on 2005-12-30
I just installed ubuntu on an AMD64 X2 with the geforce 7800 GT and the X server booted and I logged on and got on gnome with no problem.

I heard that ubuntu can detect the 'base drivers' fine, but ubuntu wont be using the card to its full potential. And that I need to install the nvidia drivers. X is working fine, would installing the nvidia drivers increase my performance?

---

### Post by erikpiper on 2005-12-30
Yes.. Have you tried games yet? Normal drivers are not using hardware acceleration...

---

