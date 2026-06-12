---
title: "Can't get X working on laptop after 8.10 upgrade"
date: 2008-11-02
forum: Multimedia Software
---

### Post by fishwebby on 2008-11-02
Hello,

I've just upgraded from Xubuntu 8.04 to 8.10 and I'm having problems with the display. When I boot now, after all the login messages the screen goes black, then switches between grey and black for a minute then just goes black. Ctrl-alt F1, F2 etc. don't do anything other than make it go grey again then back to black.

If I reboot into recovery mode (or safe mode or whatever it's called) and choose "xfix" then "resume normal boot", I can get into the graphical environment with no problems. However, if I reboot it still doesn't work. (is there any way to save whatever xfix does for the next boot?)

From other posts I've read it seems that the problem lies in /etc/X11/xorg.conf, but I'm unsure how to fix it.

I've tried playing with the X config file but without success, I even tried deleting it (I read somewhere that Xubuntu could boot without it?) but that didn't work either.

When I do run xfix and I can log in, I get a resolution of 1024x768 and all seems fine, although I'm not sure if it's using as many colours as it can etc.

As I know I can login with xfix, I know it works - I guess it's just a matter of the right config in xorg.conf.

Here's the output of a couple of commands which might help:

```
> sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 8000kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail

> sudo lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

I'm running a laptop with Xubuntu 8.10 installed.

I would be very grateful for any help anyone can offer! If you need any more information please let me know.

Many thanks
Dave

---

### Post by jimminy_cricket on 2008-11-02
Hi there,
I don't know if this is what you're dealing with but I had a similar problem after the upgrade.  Have you tried restarting X after it's done with all the flickering grey/black?  I managed to get to a debug screen, reconfigure X with
```
sudo dpkg-reconfigure xserver-xorg
```
Then after restarting X again I got a login screen.
To make the fix permanent I changed the (broken) default desktop manager setting (options --> change session).

Hope that helps.

---

### Post by fishwebby on 2008-11-02
Hi,
thanks for your reply. I tried that, and have managed to get it to display the login screen but only at 800x600, using about 75% of the screen. When I log in and go to the Display control panel it only lists 800x600 and 640x480 as possible resolutions. I know it can do 1024x768 as it does if I do the whole xfix thing. So a bit closer but still not ideal - any idea how I can get the option to change to 1024? When I run dpkg-reconfigure xserver-xorg it only asks me questions about the keyboard, nothing about the monitor.

Cheers
Dave

---

### Post by jimminy_cricket on 2008-11-02
The only other thing I could suggest is using the proprietary drivers (if there are any) for your hardware.  It's under system --> admin --> hardware drivers.  If that doesn't work i'm all out of ideas.

---

### Post by fishwebby on 2008-11-03
Hi,

alas no, it doesn't mention anything in there. Thanks for your help anyway.

Cheers
Dave

---

### Post by fishwebby on 2008-11-04
Sorted, I think - I read in this thread - [http://ubuntuforums.org/archive/index.php/t-762497.html]("http://ubuntuforums.org/archive/index.php/t-762497.html") - (3rd post from last) that somone else had a similar problem and it was solved by removing the splash screen from boot by editing the grub configuration file (actually I used the startup manager). Now I don't get the nice Xubuntu loading animation but at least it boots into X!

I think now that it works I'd rather not mess with it anymore (trying to get it working with the splash screen and everything).

Well that was a painful upgrade experience - let's hope the next one goes more smoothly!

---

