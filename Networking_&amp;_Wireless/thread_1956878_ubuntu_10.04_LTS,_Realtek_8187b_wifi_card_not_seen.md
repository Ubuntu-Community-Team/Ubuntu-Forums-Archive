---
title: "ubuntu 10.04 LTS, Realtek 8187b wifi card not seen"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by cerebralHigh on 2012-04-11
I ran the command: 
lshw -C network

And it could see the wireless card, it didn't have the driver, so I installed the windows driver using the ndiswrapper,then rebooted.
Now it can't even see the card, so I removed the driver and rebooted, still nothing.

Now when I run:

lshw -C network, all I can see is the ethernet. 
Code:
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:8f:4d:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.87 latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:50410000-50410fff(prefetchable) memory:50400000-5040ffff(prefetchable) memory:50420000-5043ffff(prefetchable)

Whatever I run in the terminal, it no longer can see the wireless card???

---

### Post by cerebralHigh on 2012-04-12
Bump :confused:

---

### Post by cerebralHigh on 2012-04-12
Can someone tell me anything??? Should I just try a fresh install?

---

### Post by cerebralHigh on 2012-04-13
This is the first time no ones responded. I would really appreciate a word of advise. Please help

---

### Post by sosostris on 2012-04-13
Hi,

I am afraid there is not much I can do for you, but I remember I had similar problems with 8187b years ago. 

Is your card USB or PCI? From what I can remember, compiling compat-wireless did a good job for me.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

If it is USB check your syslog as you unplug the stick and plug it in again. Also check lsusb if it shows the right chipset.

Last but not least, check your syslog to see if anything says firmware xy loaded. 
I remember ndiswrapper never fixed it for me.

---

