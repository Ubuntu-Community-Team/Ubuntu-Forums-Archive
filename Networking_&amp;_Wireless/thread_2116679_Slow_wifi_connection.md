---
title: "Slow wifi connection"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by magikarp555 on 2013-02-16
Hi everyone. I have a problem with my wifi usb adapter. With Windows XP it worked perfectly installing the driver with the CD. Now I needed no drivers to make Xubuntu recognize the wifi adapter, i succeded in connecting to my wifi network but it's REALLY slow. What can I do to solve this?

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by magikarp555 on 2013-02-16
Hi and thanks for your reply. I inserted that command in the terminal and obtained this:

> *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:40:00.0
       logical name: eth1
       version: 01
       serial: 00:0f:fe:24:12:ce
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:f0400000-f040ffff
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:ab:2c:48
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:1000(size=256) memory:f0500000-f05000ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 00:a0:a2:78:13:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-23-generic firmware=0.29 ip=192.168.2.7 link=yes multicast=yes wireless=IEEE 802.11bgn

See that I have an unused ethernet card. I used that when I had the LAN connection, then I started to use this wifi adapter.

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by magikarp555 on 2013-02-16
In Xubuntu there isn't gedit, there's leafpad. So i entered > gksudo leafpad /etc/pm/power.d/wireless

Then I entered "#!/bin/sh" in the document and wrote this in the terminal > /sbin/iwconfig wlan0 power off

but i obtained this > Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by magikarp555 on 2013-02-16
I've put "sudo" in front of that command and now it gives me no errors but apparently nothing happens. I think I didn't understand the Wild Man's post.
Should I enter that command in the document or in the terminal?

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by magikarp555 on 2013-02-16
I followed the instructions but then when I insert the command > sudo modprobe -rfv rt2800usb

the computer crashes. What should I do?

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by magikarp555 on 2013-02-16
No, it's always slow also if I add only that line.. Anyway I still don't understand why inserting this command > sudo modprobe -rfv rt2800usbmy computer crashes.

Don't know if this can help but when I insert this line > echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf

The output is this > options rt2800usb nohwcrypt=1


---

### Post by magikarp555 on 2013-02-19
Does anyone know what I can do to solve this?

---

