---
title: "ATI driver issue (yes, another one)"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by Coty on 2007-09-28
Well, I'm running Ubuntu 7.04 with kubuntu-desktop package installed, beryl (not auto-starting), an ex-installation of fglrx (tried to uninstall the kernel modules, "modprobe -r fglrx", but modprobe -l still lists fglrx.ko)... and I have an ATI Radeon 9550 video card.

With fglrx, any OpenGL-based application runs slower than running with vesa driver, including glxgears... So I've thought of reverting to the ati driver. Got that working, too, so I'vre run beryl, restarted Xserver a couple of times, even rebooted the system and everything was working properly. But, after I've turned off the computer and (after a while) turned it on again, Xserver didn't start properly (the usual black screen and frozen system)

It's not the first time this happens to me, and I don't know how is it possible. I mean, in the meantime the configuration files haven't changed... is the kernel doing something special at turn-off ? (I am sure it doesn't, but I simply can't figure out the problem... :confused: )

Thanks!

---

### Post by w4ett on 2007-09-29
Taking a shot here:  You might try doing a

```
sudo apt-get remove fglrx
```

and then a

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

to remove fglrx modules and then to reconfigure your xorg.conf

---

