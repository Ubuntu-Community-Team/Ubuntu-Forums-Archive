---
title: "EW-7711UAn wireless card not finding any networks"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by weliwarmer on 2010-08-12
Hi,

I've a working internal Intel wifi card but it does not have the greatest of ranges so I bought a Edimax EW-7711UAn.

On the box is says Linux compatible.  All knowing Google states that it works out of the box with Ubuntu 10.04.

NetworkManager lists the card at a Ralink 8011.n WLAN (disconnected).

There are no networks listed under this card in NetworkManager or wicd even if I disable the internal wifi using the nm-system-settings.conf.

dmesg has the following lines:

```
[ 1441.132195] usb 1-8: new high speed USB device using ehci_hcd and address 6
[ 1441.281693] usb 1-8: configuration #1 chosen from 1 choice
[ 1441.319978] phy3: Selected rate control algorithm 'minstrel'
[ 1441.324292] Registered led device: rt2800usb-phy3::radio
[ 1441.324395] Registered led device: rt2800usb-phy3::assoc
[ 1441.325110] Registered led device: rt2800usb-phy3::quality
[ 1441.356913] rt2800usb 1-8:1.0: firmware: requesting rt2870.bin
[ 1441.563233] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

The led flashes quickly a few times when I plug it in then once a second after that.

The firmware rt2870.bin is in /lib/firmware/

I've even gone old-school and tried compiling the newest driver from Ralink but this fails with...

```
/home/tim/Desktop/temp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1134: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/tim/Desktop/temp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.o] Error 1
make[1]: *** [_module_/home/tim/Desktop/temp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [LINUX] Error 2

```

Any more ideas would be most appreciated.

Thanks,
Tim

---

### Post by lwhitmore on 2010-09-15
Same problem here.

---

### Post by lwhitmore on 2010-09-15
Okay .. found a solution.

I downloaded the latest drivers from Ralink website (rt3070) and used a patch supplied by a user in this thread ([http://ubuntuforums.org/showthread.php?t=1285828&page=11](http://ubuntuforums.org/showthread.php?t=1285828&page=11)).

The names of two functions have changed in the latest kernel (used in ubuntu 10.10).  The patch addresses the change and allows successful compilation.

After installation my Edimax EW-7711UAn works as well as previously.

PS.  I blacklisted the following (via /etc/modprobe.d/blacklist.conf):

blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt2870sta

---

