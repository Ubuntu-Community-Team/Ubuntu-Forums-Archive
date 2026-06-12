---
title: "ATI 8.42.3 mesa problem"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by templarrush on 2007-12-09
I just installed the new ATI driver 8.42.3
And now I get the mesa things when I enter fglrxinfo in the terminal

display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

When I try to enable Compiz my screens goes white.
Anyone has a solution to solve this?

I've read these things solve it but the first command gives an error already

$ sudo rmmod fglrx
$ cd /lib/modules/*/misc
$ sudo insmod fglrx.ko
$ modprobe fglrx

i'm on gutsy :)

---

### Post by templarrush on 2007-12-10
someone ?

---

### Post by acoustibop on 2007-12-10
Try this, from the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page"), templarrush:
```
Create the following folder

sudo mkdir /lib/modules/$(uname -r)/volatile

Note: the volatile directory might already exist at this stage then simply continue with the next step.

Create a symbolic link

sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko


NOTE : On my Gutsy install, after a reboot this link was always removed automatically leaving me without an fglrx module loaded, and thus no ATI rendering. There have been several ways of getting around this suggested here, and here is the one that worked for me:

sudo gedit /etc/init.d/ati-module-fix

And put this in it:

#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0


Make it executable

sudo chmod ugo+x /etc/init.d/ati-module-fix

Now, make this run before gdm (which starts with sequence number 13)

sudo update-rc.d ati-module-fix defaults 12

It is possible that gdm sequence number is different. To find the gdm sequence number:

ls /etc/rc2.d/

And substitute 12 in the previous command with gdm sequence number - 1.
```

Works for me, provided the driver is properly installed.  BTW I'd recommend the Unofficial Wiki methods (see the history tab for older drivers) for installing fglrx drivers: they've always worked beautifully for me.  It may seem more complicated than other methods, but it's actually quite simple: all you have to do is paste and copy lines, and make a few simple decisions, such as: have you already installed an fglrx driver?  I'd also recommend trying the current 7.11 driver.

---

