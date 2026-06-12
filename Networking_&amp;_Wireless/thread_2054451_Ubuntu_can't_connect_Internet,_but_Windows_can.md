---
title: "Ubuntu can't connect Internet, but Windows can"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by norwaythai on 2012-09-07
I have changed my network card, and it works well in Windows without any setting, but in Ubuntu it does not work, what can I do?

Thanks

---

### Post by norwaythai on 2012-09-08
I deleted the file /etc/udev/rules.d/70-persistent-net.rule, but the file wasn't created after I restart the computer.

I use the command [COLOR="Red"]ifconfig -a[/COLOR] to see the mac address being ff:ff:ff:ff:ff:ff

I typed the command [COLOR="Red"]sudo lshw -class network[/COLOR], the result is


  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: ff:ff:ff:ff:ff:ff
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=no maxlatency=32 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:ec010000-ec0100ff memory:28000000-28007fff

---

### Post by kimberlite on 2012-09-08
Do you have network manager applet in your panel? If so, right click and enable wired connection. If it is not working, try issue the following command: ```
sudo ifconfig eth0 up
``` in a terminal. You may also want to consult with this [thread]("http://ubuntuforums.org/showthread.php?t=1490833").

---

### Post by norwaythai on 2012-09-08
The command sudo ifconfig eth0 up does not work.

I follow the guide [http://www.ehow.com/info_12058752_networking-disabled-ubuntu.html]("http://www.ehow.com/info_12058752_networking-disabled-ubuntu.html"), and the result is [COLOR="Red"]If the device was working, then stopped, the problem is probably hardware-based, or the kernel module for that device was disabled.[/COLOR], but in Windows the NIC works well, so probably it's the problem with the kernel module for the NIC.

by the way, the network does not work in the Ubuntu demo running in the Ubuntu CD

---

### Post by norwaythai on 2012-09-08
my nic is rtl8139d, is it incompatible with Ubuntu 11.04?

---

### Post by norwaythai on 2012-09-08
As expected, this problem is hardware-based. I bought a new NIC and replaced this one, and it works well in both Windows and Ubuntu.

Thanks anyway!

---

