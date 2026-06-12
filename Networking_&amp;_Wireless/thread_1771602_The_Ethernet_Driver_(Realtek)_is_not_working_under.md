---
title: "The Ethernet Driver (Realtek) is not working under Natty, after it was OK in 10.10"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by amanjpro on 2011-05-30
Hello all,

Today I realized that my newly installed Natty does not recognize the Ethernet port, I used to have it when I was working on the Ubutnu 10.10.

The following is the output (only the network related part) of lshw command:

```
-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: c8:0a:a9:f6:6d:8a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
                resources: irq:45 ioport:2000(size=256) memory:d1004000-d1004fff

```

Is there any solution for this? I really need this to be fixed otherwise Natty and all its awesomeness will mean nothing for me :(

---

### Post by amanjpro on 2011-05-30
Thanks everybody for your intentions to help, it turned out that the issue is a hardware issue and I could solve it by simply removing the battery and inserting it back after 10 mins or so, I know it is stupid, but that is how my hardware works :D

---

### Post by mn_voyageur on 2011-05-31
I am having the same problem.  Why did this work?  (I'm still on 10.10.)

MarkN

---

### Post by MartyBuntu on 2011-06-01
Are you dual booting with Windows?

---

### Post by mn_voyageur on 2011-06-01
> **MartyBuntu said:**
> Are you dual booting with Windows?

Nope.  Just Ubuntu.  

It worked a few days ago.  The only thing I have done is switched routers.  I am using an older Linksys.  I played with a friend's NetGear Gigabit Router and then returned it to him.

Could this have been the problem?  The Linksys is a 10/100.  Is the port waiting for another gigabit switch?

MarkN

---

### Post by Toz on 2011-06-01
Just reading about this in another post. A bug report exists with workarounds: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

---

