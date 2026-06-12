---
title: "[SOLVED] Stealing xorg.conf file"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by radiocognition on 2008-01-09
Hey Everybody:

I really screwed up my system's graphics when trying to install a graphics card.  I gave up on the installation and am just trying to get the graphics back to where they were before I started.  After messing around withs the Screens and Graphics prefrences, I became frustrated at just blindly guessing what drivers I was supposed to use (my system was using the vesa drivers in graphic safe mode).  I tried booting on my live CD just to see what ubuntu was trying to use, and to my surprise, Ubuntu was supposedly using the same drivers (though I have my doubts with this new Screens and Graphics panel).  Ive already tried```
sudo dpkg-reconfigure xserver-xorg
``` a few times with little success.  Can I just boot the Ubuntu live cd on my system, copy the xorg.conf file, and use that on my installed system?  Any advice or help would be appreciated

---

### Post by taurus on 2008-01-09
You first need to mount your harddrive where / is located.  Then, you can try copying /etc/X11/xorg.conf from the LiveCD over to your harddrive.  _Assuming_ / is on /dev/sda1, you can try something like this from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
sudo cp /media/ubuntu/etc/X11/xorg.conf /media/ubuntu/etc/X11/xorg.conf.bak
sudo cp /etc/X11/xorg.conf /media/ubuntu/etc/X11/xorg.conf
sudo umount /media/ubuntu
```
Now, reboot without the LiveCD in the drive.

---

### Post by radiocognition on 2008-01-09
That did the trick.  I made a copy of the xorg file for the future so I can do the same trick again without having to reboot.  From now on, I will be working with the xorg.conf file, I find Ubuntu 7.10's Screen and Graphics panel buggy to say the least.  Hopefully the issues will be ironed out in the next release.

---

