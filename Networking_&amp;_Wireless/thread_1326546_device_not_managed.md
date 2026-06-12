---
title: "device not managed"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Hakimjo on 2009-11-14
My network manager under 9.10 indicates that my Ethernet "device not managed" (périphérique non géré).  The ethernet socket does blink and the wireless works fine.  My system is a Lenovo desktop and it did work flawlessly most of the time under 9.04.  What do I need to do to make network manager manage my device ?

Thanks

---

### Post by Iowan on 2009-11-14
Check */etc/network/interfaces*. If the device is listed there, the simplest way is to edit the file ```
sudo nano /etc/network/interfaces
``` or  ```
gksudo gedit /etc/network/interfaces
``` and comment out the lines defining the interface - leave the two lines for "lo".

---

### Post by Hakimjo on 2009-11-15
Thanks, this does the trick for the "device not managed".  It also gave me a default connection once.  But I still can't establish the dsl connection.

/etc/network/interfaces now looks like this: 
auto lo
iface lo inet loopback

##auto dsl-provider
##iface dsl-provider inet ppp
##pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
##provider dsl-provider

##auto eth0
##iface eth0 inet manual

---

### Post by MrSkrimps on 2009-11-20
Thanks! this worked for me as well :)

---

### Post by matt06 on 2009-12-03
> **Iowan said:**
> Check */etc/network/interfaces*.

Thanks for this.  I'm running Xubutu 9.10 here and had this problem with my onboard nic ('8139too' according to NM now).  I edited /etc/network/interfaces as well and a restart took care of it.

What is the difference between this fix and [the one posted in another thread]("http://ubuntuforums.org/showpost.php?p=7612600&postcount=7")?

[http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

> edit /etc/NetworkManager/nm-system-settings.conf
change "managed=false" to "managed=true"

---

### Post by rachael4u on 2009-12-03
thnxxxx for the info..

---

### Post by Iowan on 2009-12-03
I'm not completely sure what the referenced threads do - possibly tell Network Manager to control the interface in spite of its being defined in */etc/network/interfaces*. By removing the definition from that file, Network Manager will control it by default.

---

### Post by caironet16 on 2010-02-12
Thanks this fixed it for me too.

Yea I'd say that because the file didn't have those lines commented out Gnome was just like "k all urs" hence the stuff about it being managed when you try and view info on it from Gnome.

---

### Post by OldManRiver on 2011-08-05
NOT WORKING

This is not fixing it for me at all.

I had actually edited 4 files before looking this up:

/etc/network/interfaces
/etc/dhcp3/dhcpd.conf
/etc/resolv.conf
/etc/sysctl.conf

Need something much more definative.

Thanks!

OMR

---

