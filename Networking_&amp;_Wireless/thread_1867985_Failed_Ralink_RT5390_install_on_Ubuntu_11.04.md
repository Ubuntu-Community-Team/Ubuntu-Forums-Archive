---
title: "Failed Ralink RT5390 install on Ubuntu 11.04"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by nichol7 on 2011-10-23
Hi everyone.

This is my first post on this forum.  Hopefully you will forgive any blunders I may make as I am very much a newbie.

Some background first.  I have an HP mini netbook that I have installed ubuntu 11.04 on.  Everything is working fine except the wireless connection.  I have a Ralink RT5390 chipset.  I was able to find a thread on this forum that details the steps required to get the 5390 driver working.  It is listed below:

[http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)

I followed the steps outlined in the forum but did not get a successful build.  I searched around a little only to realize that the Ralink driver on their site had been updated & that the SUSE patches also pointed to a newer version.  I basically applied the rt5390sta-2.5.0.3-* series of patches before I realized my mistake (should be 2.4.0.4-* patches)

With some work I was able to find the original 2010_* code from the following site:

[http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/)

Again I followed the steps outlined in the above thread, this time getting all the way to the end without issue (or so I thought).  After a reboot, my wireless is still not working.  I examined the kern.log file I see the following line:

"rt5390sta: disagrees about version of symbol module_layout"

When I run a uname -r I get : 2.6.38-11-generic
A uname -m gives: i686

At this point I am unsure of how to proceed.  I assume that I have to remove the old module from the kernel & build another but am unsure of how to do this.

Any help would be greatly appreciated.

---

### Post by praseodym on 2011-10-24
Try this installation with dkms:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/3473742/Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3 
```
From here:
[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)

---

### Post by nichol7 on 2011-11-01
Thanks for the help on this.  I have since been able to get my wireless up and running.

---

### Post by XxionxX on 2011-12-17
I am glad you were able to get it working. Could you be so kind as to link the resource(s) you used to solve this problem? I would be very grateful.

---

