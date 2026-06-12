---
title: "lirc not changing channels"
date: 2007-11-19
forum: Mythbuntu
---

### Post by kbarter on 2007-11-19
Last weekend I had the opportunity to install Mythbuntu for the first time after the hard drive in my Gentoo based mythtv system died.

Everything went smoothly, up until I tried to get lirc working.  When the channel change script runs, the LED on my IR blaster blinks, but the channel will not change.

I had lirc setup up previously under Gentoo, and it all worked good.  To the best of my knowledge, all of the config is the same.  The lircd.conf is the same, the channel change script is the same, etcetera.

Does anyone have any idea why the IR blaster will light the LED, yet now be able to change the channel?

Thanks

---

### Post by OffAxis on 2007-11-20
The LED on the blaster will light up when your channel changing script (the irsend command, specifically) is passed a variable that corresponds to a remote section of the lircd.conf

So, could be an error in the lircd.conf file.
is the lircd.conf a copy of the one that was on your gentoo system or did you rebuild it?
If it's not the original one, you might have gotten a .conf for your set-top-box with some different frequencies declared in the remote section (even though it was labeled as the same model number).

Is the correct remote specified in the channel changing script?

```
irsend LIST "" ""
```
will show you the viable remote sections from lircd.conf

---

### Post by kbarter on 2007-11-20
I double checked, and the lircd.conf is exactly the same as what was working previously on Gentoo.  I took a copy of it from a backup, and did a diff, just in case...

Using irsend LIST "" "" does show the correct remote as well.

Is there something else I could be missing?

Thanks

---

### Post by OffAxis on 2007-11-21
Is it the exact same channel changing script as before?
 -->Is the correct remote device referenced in this file?


Can you change the channel using irsend directly?

```
irsend SEND_ONCE [your remote device name from lircd.conf] [channel #]
```

What kind of blaster are you using? A serial,usb or an integrated one like the PVR-150?

---

### Post by CompEngr on 2007-11-21
Unfortunately kbarter is experiencing the same problem that I have.  And after scouring the forums for a good long while the answer is this...
Lirc 0.8.2 is broken for ir serial transmitters on Gutsy.  I did a search on the kernel version and lirc version and this seems to be happening to other also.

Most of the people I have read about have installed custom versions of lirc 0.8.3 to solve the problem.  Is this the answer... I hope not.  I hope that a real solution could be forth coming.

---

### Post by OffAxis on 2007-11-21
Okay. I thought since the blaster was transmitting that it was reading the device properly and it was just a configuration issue.
Thanks for the edification CompEngr.

The lirc instructions for obtaining the latest build
[http://lirc.org/cvs.html]("http://lirc.org/cvs.html")

and the build tools you'll also need to have installed

automake1.10
libtool
autoconf

---

