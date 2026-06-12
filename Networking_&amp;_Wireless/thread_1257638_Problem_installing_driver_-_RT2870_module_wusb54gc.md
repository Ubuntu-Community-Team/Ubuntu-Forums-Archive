---
title: "Problem installing driver - RT2870 module wusb54gc v3"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by grayhatter on 2009-09-04
I'm trying to setup my WUSB54GC USB wireless on Ubuntu 9.04.

I followed the brilliant guidance of radixor (see thread [http://ubuntuforums.org/newthread.php?do=newthread&f=336](http://ubuntuforums.org/newthread.php?do=newthread&f=336)), and most of the steps seem to work well however when I compile and install the driver it doesn't seem to take the updated device setting.  I'm lost and would appreciate any help.

I've downloaded and installed the drivers per the thread above, installed the module, however when i run 'modinfo rt2870sta | grep 1737' it's not there.  Not sure what I'm missing.

I read through the forum and the sticky, I've gone through the make files and not seeing the problem.



Maybe this helps?
root@desktop-lnx:/home/user1/wlan# modinfo rt2870sta | grep 1737
root@desktop-lnx:/home/user1/wlan# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
alias ra0 rt2870sta
root@desktop-lnx:/home/user1/wlan# cd /etc/Wireless
root@desktop-lnx:/etc/Wireless# ls
RT2870STA  RT2879STA
root@desktop-lnx:/etc/Wireless# ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device
root@desktop-lnx:/etc/Wireless# lsmod | grep rt2870sta
rt2870sta             506324  0 
root@desktop-lnx:/etc/Wireless# ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
root@desktop-lnx:/etc/Wireless# cat /home/user1/wlan/include/rt
rt2870.h        rt_config.h     rtmp_def.h      
rt28xx.h        rt_linux.h      rtmp.h          
rt_ate.h        rtmp_ckipmic.h  rtmp_type.h     
root@desktop-lnx:/etc/Wireless# cat /home/user1/wlan/include/rt2870.h | grep Linksys
	{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */		\
root@desktop-lnx:/etc/Wireless#

---

### Post by grayhatter on 2009-09-07
Any tips or links to documentation I can read to research this?  Dead in the water at this point.

---

