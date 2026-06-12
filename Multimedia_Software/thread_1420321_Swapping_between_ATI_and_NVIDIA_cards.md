---
title: "Swapping between ATI and NVIDIA cards"
date: 2010-03-02
forum: Multimedia Software
---

### Post by roddomi on 2010-03-02
Hello,

I am running Ubuntu 9.10. My work requires me to frequently swap video cards between an ATI Radeon 5870 card and an NVIDIA GeForce 8800 GTX card. My question is: can the ATI driver (fglrx - catalyst 10.2) and the NVIDIA driver (nvidia 190.29) co-exist? Or do I need to reinstall the driver every time I change the card? I would like for the drivers to be able to co-exist so it would only be a matter of restarting my machine with the new card and choose the right xorg.conf file (perhaps from the GRUB menu). Is this possible?

Thank you,

Rodrigo

---

### Post by handy on 2010-03-03
I have seen a post on the Arch forum where someone had made a script that allowed them to choose between two different graphic cards.

I'll have a look & see if I can find it again.

If you can't deal with bash script, I'm sure that if a I post it here someone will help you.

First things first though, I need to find it for you. :)

---

### Post by handy on 2010-03-03
No, sorry, it is a script for choosing between two xorg.conf files re. twin screen output, though I suspect it should be able to be used with little modification for your purposes, I hope?

[http://bbs.archlinux.org/viewtopic.php?pid=712359#p712359](http://bbs.archlinux.org/viewtopic.php?pid=712359#p712359)

:D

---

### Post by handy on 2010-03-03
If you do get this to work for you, please post back here with the code so others can benefit from your experience?

Thanks. :)

---

### Post by Yellow Pasque on 2010-03-03
I think it may be possible if you make sure fglrx's libGL.so and libglx.so aren't overwritten when you install the nvidia driver. You would also need to direct the nvidia driver to its version of these files in xorg.conf (I know that's possible, but don't remember the exact syntax off the top of my head).

---

### Post by handy on 2010-03-03
> **Temüjin said:**
> I think it may be possible if you make sure fglrx's libGL.so and libglx.so aren't overwritten when you install the nvidia driver. You would also need to direct the nvidia driver to its version of these files in xorg.conf (I know that's possible, but don't remember the exact syntax off the top of my head).

So the script in the thread I posted previously doesn't solve the problem?

---

### Post by Yellow Pasque on 2010-03-03
> **handy said:**
> So the script in the thread I posted previously doesn't solve the problem?
It allows easy switching between two xorg.confs, so it might be useful, but it doesn't solve the issue with making sure ATI and Nvidia's proprietary versions of the GL/GLX shared libraries play nicely together.

---

### Post by handy on 2010-03-03
> **Temüjin said:**
> It allows easy switching between two xorg.confs, so it might be useful, but it doesn't solve the issue with making sure ATI and Nvidia's proprietary versions of the GL/GLX shared libraries play nicely together.

Can they be separated into different directories & linked to via script.

Can that work?

---

### Post by roddomi on 2010-03-03
Yes, this works!

For the GRUB part, I setup a script (DriverSelect.sh) that runs at boot-time as explained on this post:
[http://ubuntuforums.org/archive/index.php/t-1287967.html](http://ubuntuforums.org/archive/index.php/t-1287967.html)

For the libraries, I copied the NVIDIA and ATI files for libGL and libglx to a directory outside /usr/lib (f.e. /usr/{nvidia,ati}) and modified DriverSelect.sh to copy the files and create the symbolic links. Here's my DriverSelect.sh:

```
#!/bin/sh
if grep -q nvdriver /proc/cmdline
then
    # setup xorg.conf
    cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf

    # setup libGL
    cd /usr/lib
    rm libGL.*
    cp /usr/nvidia/libGL.la .
    cp /usr/nvidia/libGL.so.190.29 .
    ln -s libGL.so.190.29 libGL.so.1
    ln -s libGL.so.1 libGL.so

    # setup libglx
    cd /usr/lib/xorg/modules/extensions
    rm libglx.*
    cp /usr/nvidia/libglx.so.190.29 .
    ln -s libglx.so.190.29 libglx.so
else
    # setup xorg.conf
    cp /etc/X11/xorg.conf.fglrx /etc/X11/xorg.conf

    # setup libGL
    cd /usr/lib
    rm libGL.*
    cp /usr/ati/libGL.so.1.2 .
    ln -s libGL.so.1.2 libGL.so.1
    ln -s libGL.so.1.2 libGL.so

    # setup libglx
    cd /usr/lib/xorg/modules/extensions
    rm libglx.*
    cp /usr/ati/libglx.so .
fi
```

Thanks for your help!

Rodrigo

---

### Post by handy on 2010-03-03
I love it when a plan comes together! ;)

Well done Rodrigo, & thanks for posting your solution, it is bound to help someone else. :)

---

### Post by sv1etk on 2011-05-03
> **handy said:**
> I love it when a plan comes together! ;)

Well done Rodrigo, & thanks for posting your solution, it is bound to help someone else. :)

It did! Me!
I had done something similar.
I copied custom directories the important files (libs, xorg drivers, etc) and in each system startup I run a script (/etc/rc2.d/S01VideoCard) which checked which videocard is active
(lspci |grep "VGA Compatible Controller: ATI" or "...: nVidia") and 
copied the appropriate files and the correct xorg.conf.

The problem is, that when I reached X (through gdm), I should login and the crash the server (ctrl-alt-backspace). When I did that the correct driver was loading. If I didn't do that, the driver was usualy the nouveau or radeon (yes, I have them blacklisted, i have made an initrd... I almost tried to shoot my drive to get rid of them! Then I learned about plymouth!)

---

