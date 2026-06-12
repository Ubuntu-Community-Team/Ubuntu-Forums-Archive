---
title: "Ralink RT5390 in Ubuntu 11.10"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by niceplace on 2011-10-14
This is the information that I have about the card:
Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]

Ubuntu 11.04 did not recognize and I had to follow a tutorial in which i needed to install some patchs and a driver. The tutorial is: [http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)
 
Now Ubuntu 11.10 recognize the wireless card but it do not work properly. What happen is: It connects and disconnects every time, until I reconnect and the connection just works for a few seconds. 

I think the problem is from the kernel, because in Fedora 16 (beta with new kernel) happen the exact same problem.

---

### Post by richleasure on 2011-10-16
I had the same problem when I upgraded my HP DM1Z laptop from 11.04 to 11.10, but it was easy to fix.

Under 11.04 I got my Wi-Fi working using [these instructions]("http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010") on 6by9.net. For 11.10 I had to comment out "rt5390sta" in /etc/modules and "blacklist rt2800pci" in /etc/modprobe.d/blacklist.conf. After a reboot my Wi-Fi came right up.

Hope this helps.

---

### Post by niceplace on 2011-10-16
It worked for a while. But now it is having the exact same problem.

---

### Post by Praetor77 on 2011-10-25
This leads to using the stock drivers which are quite buggy.

You can download and install the OpenSuse package following these instructions...

[http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010](http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010)

---

