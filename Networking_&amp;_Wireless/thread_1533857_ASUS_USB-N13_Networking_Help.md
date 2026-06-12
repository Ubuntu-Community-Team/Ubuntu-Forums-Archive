---
title: "ASUS USB-N13 Networking Help"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by Saint- on 2010-07-18
Hello,
I have been looking at the other threads about the N13 around here but no matter what I try I can't get wireless! 
Can someone guide me through how to get it working?

---

### Post by Xonnie316 on 2010-07-18
I'm another Asus N-13 USB Owner which is trying to install it on Ubuntu 10.4.

I'm experiencing the same issues installing it...

I followed post #35 from redsultan's thread ([http://ubuntuforums.org/showpost.php?p=8958958&postcount=35](http://ubuntuforums.org/showpost.php?p=8958958&postcount=35))

After typing in **make install** this error shows up about file & folder permissions

> 
make -C /home/shaun/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': Permission denied
make[1]: Entering directory `/home/shaun/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
mkdir: cannot create directory `/etc/Wireless/RT3070STA': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/shaun/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
make: *** [install] Error 2

Any suggestions people??

And when I tried to add the code to the 2 following files, it doesn't allow me to save regarding permissions aswell:

gedit /etc/udev/rules.d/network_drivers.rules
gedit /etc/modprobe.d/network_drivers.conf

I had a look at my account and it seems like its admin, coz this is the user I installed Ubuntu with...

---

### Post by Saint- on 2010-07-18
> **Xonnie316 said:**
> I'm another Asus N-13 USB Owner which is trying to install it on Ubuntu 10.4.

I'm experiencing the same issues installing it...

I followed post #35 from redsultan's thread ([http://ubuntuforums.org/showpost.php?p=8958958&postcount=35](http://ubuntuforums.org/showpost.php?p=8958958&postcount=35))

After typing in **make install** this error shows up about file & folder permissions



Any suggestions people??

And when I tried to add the code to the 2 following files, it doesn't allow me to save regarding permissions aswell:

gedit /etc/udev/rules.d/network_drivers.rules
gedit /etc/modprobe.d/network_drivers.conf

I had a look at my account and it seems like its admin, coz this is the user I installed Ubuntu with...
 I have tried this and it was the exact same error for me. Any help people?

---

### Post by Xonnie316 on 2010-07-18
I'm not at home at the moment to test this out.

But this looks like the solution, read this post:

[http://ubuntuforums.org/showpost.php?p=9599830&postcount=7](http://ubuntuforums.org/showpost.php?p=9599830&postcount=7)

---

### Post by Xonnie316 on 2010-07-19
I tried it out last night, and it was a success!

Wireless is working !!

---

