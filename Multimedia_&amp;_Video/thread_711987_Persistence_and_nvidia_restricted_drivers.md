---
title: "Persistence and nvidia restricted drivers"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by gopher38 on 2008-03-01
Hello all,

I've a question regarding running off the LiveCD with persistence (on a USB flash drive) and restricted drivers.  First, very quick background info.  I'm new to Linux and wanted to try out Ubuntu with Vista on my HP DV9628 machine. After a bit of playing, I got most things to work, but I messed up my MBR in the process.  Also, I read about this LiveCD with persistence feature and thought to myself, “hey, great idea to test out Ubuntu without touching my setup” (which is, of course, one of their goals).

Anyway, I started down that path, and I must say, I'm pretty impressed so far.  I've been able to get wireless working on it, installed new packages, connect to the network, added quite a bit of stuff, and it's all sticking so far, with one exception.  Runs slower, but not so bad; and I don't care about the speed anyway.

The one exceptions is the monitor.  I can't only get livecd to run in safegraphics mode, with the best resolution being 1024x768.  This machine has the Nvidia card with GeForce 7150, I believe.  Interestingly, I did get it working in 1440x900 with the Nvidia card when I was doing a full installation, so it is theoretically possible.  With LiveCD, when I check the use restricted drivers box for Nvidia, it will not stay checked.  Next time I log in, it is unchecked again.  I've tried logging in as root, but that didn't change it (normally I run under a new user with admin priviledges).  Also, I tried following this tutorial, ([http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)) 

  sudo /etc/init.d/gdm stopsudo
  dpkg-reconfigure xserver-xorg
  sudo /etc/init.d/gdm start
  
but upon gdm restart, I got a message

  There appears to be an Xserver already running on display 0

I have only a fleeting grasp of what's going on (as I said, pretty new to  Ubuntu/Linux), but could it be that, when booting off of LiveCD, it always starts with the Ubuntu/LiveCD account, which can't run the restricted drivers (so they get turned off), and then goes to the new admin account? If anyone has any ideas, I'd like to hear them.  thanks.

---

