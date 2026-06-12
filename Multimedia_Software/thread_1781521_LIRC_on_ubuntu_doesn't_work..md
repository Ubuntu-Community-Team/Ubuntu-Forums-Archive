---
title: "LIRC on ubuntu doesn't work."
date: 2011-06-13
forum: Multimedia Software
---

### Post by rand64 on 2011-06-13
I'm a long time gentoo user, but I have used the ubuntu minimal cd to set up an htpc.  I made a homebrew ftdi receiver and I use my harman kardon stereo remote with it.  The receiver and remote work perfect on my gentoo workstation, but don't work on ubuntu.  Both ubuntu and gentoo are running the same version of lirc.  I used ps aux | grep lirc to confirm that both systems are executing the exact same command to start lirc.  Still irw shows me nothing.  I tried to use irrecord to remake the config file, and it crashes with the usual "something is wrong" when you give it the first button.  So, I ask, what the hell is wrong with ubuntu?  I know it isn't my configuration, this same hardware works perfect on gentoo.  The only other real difference is the kernel version.  My gentoo is on 2.6.34 and ubuntu is on 2.6.38.  I also checked that they both have the same version of libftdi.  I don't want to regret trying what is supposed to be the easiest of the linux distributions...

---

### Post by rand64 on 2011-06-13
Well I built lirc from source and changed the baud rate in the ftdi driver from 9600 to 2400 and it works fine now.  Just in case anyone else has a problem with the ftdi driver.

---

