---
title: "Can't boot into KDE w/ nVidia after Feisty upgrade"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by anachreon_ on 2007-05-07
Hi all,

Usually, when I upgrade Kubuntu on my machine with a GeForce 7600 GT, I always get kicked to a TTY upon restart, where I have to reinstall the nVidia proprietary drivers using Alberto Milone's Envy script.  After that, things work peachy.

After upgrading to Feisty and rebooting, I was taken to a terminal rather than KDE, as usual.  I had already downloaded and installed the new version of Envy, so I cleaned the old install of the nVidia driver and installed it again.  However, KDE won't start now.  Here is all I get :

```

sudo :/etc/init.d/gdm: command not found
Stopping K Display Manager: kdm
Starting K Display Manager: kdm

```

It just leaves me at a command line.  

I tried reconfiguring my xorg.conf by running "sudo dpkg-reconfigure xserver-xorg, thinking some settings from Beryl might be messing things up, but this didn't help.

Can't think of what I messed up here.  I recall at one point the terminal says something about "--composite" being unrecognized.  Any ideas?  Any help GREATLY appreciated!

---

### Post by anachreon_ on 2007-05-07
Update :

Ok, when I try "sudo startx" I get the following errors :

```

(EE) Unable to find a valid framebuffer device
(EE) NV(0): FAiled to open framebuffer device, consult warnings and/or errors above for possible reasons

```

Anybody know what might have gone wrong?  Should I use Envy to uninstall the nVidia proprietary drivers and then just install nvidia-glx to see if I can get X started?  I'm sort of surprised dpkg-reconfigure xserver-xorg didn't solve the issue - seems to be something with my xorg.conf.

Any help appreciated.

---

### Post by ajgreeny on 2007-05-07
Are you using gdm or kdm when you boot?  Perhaps trying the other one (whichever you are not using) by doing *sudo dpkg-reconfigure gdm* and changing your wm.

---

