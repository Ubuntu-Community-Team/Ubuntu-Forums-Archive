---
title: "ATI video card"
date: 2009-05-13
forum: Multimedia Software
---

### Post by snkngshps on 2009-05-13
When I first upgraded to Jaunty (when it was still in beta), my ATI graphics card apparently wasn't compatible and instead of being able to login to my desktop I was getting crazy distorted screens and wasn't able to do anything.

With the help of the people on [this thread]("http://ubuntuforums.org/showthread.php?t=1108351") I was able to work-around the problem, but I think it was done so by disabling the graphics card driver. My question is, is there a driver that is compatible with my graphics card (detailed in my signature) that will work in Jaunty? Here are the steps I took, with the advice of those in the thread.

I deleted the xorg.conf file by running:

```
sudo rm /etc/X11/xorg.conf
```

Then I removed the fglrx driver:

```
sudo apt-get purge xorg-driver-fglrx
```

Since then I've been able to log in but I still get occasionally distorted screens and often times while watching videos, the playback will lag or distort. This only last for a second or two,  but this tells me that I'm probably not running my graphics card correctly. Any ideas on what I should do to get this fixed up? Thanks!

---

### Post by Dimarchi on 2009-05-13
The /usr/share/ati has fglrx stuff if you have not deleted the driver the way Ati recommends it (by running the fglrx-uninstall.sh - this is only true if you have installed the version downloaded from the Ati site...for the version installed from the repositories the apt-get purge is the way to go).The way to regenerate a brand new xorg.conf is to type

sudo dpkg-reconfigure -phigh xserver-xorg

in the console and reboot. That should bring you to the default state. That much I can say for certain. What I am not certain of is this: upgrading along the way from beta to released version may have left some stuff in your system that still affects you in a way that a cleanly installed released version does not. People who have experience with this can help you better than I can.

---

### Post by snkngshps on 2009-05-13
Ok, I regenerated the new xorg.conf. Do I need to do anything else as far as reinstalling a driver?

---

