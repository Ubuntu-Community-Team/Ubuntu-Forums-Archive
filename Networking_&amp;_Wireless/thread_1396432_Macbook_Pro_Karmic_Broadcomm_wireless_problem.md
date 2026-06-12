---
title: "Macbook Pro Karmic Broadcomm wireless problem"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by tonycolin on 2010-02-02
My wireless was working perfectly until I accidentally let the battery run flat with the machine prevented from hibernating. Upon recovery, there was no wireless available. Checking the Hardware Drivers, I can see the Broadcomm driver as "Activated but not currently in use". Following the copious advice elsewhere I have disabled the driver, rebooted the machine, enabled it again - many times. Still the same message. What is stopping me from activating it? Bit of a noob so........

Macbook Pro 5.5, Ubuntu 9.10

---

### Post by kensanx on 2010-02-24
I'm having the same issue. This is what I get from lshw -C network

*-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:93200000-93203fff

Wired connection works, but there is no interface coming up with iwconfig.

I tried reinstalling bcmwl-kernel-source package a couple of times and it worked, although after restarting, it would stop working again. But now it's not working anymore. Has anyone else run into this issue?

---

