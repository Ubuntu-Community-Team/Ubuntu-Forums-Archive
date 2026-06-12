---
title: "Wireless not working on Acer Aspire One D150"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by Andyvanman on 2010-03-22
Hi all

I had UBR installed and working fine for a month or so, wireless and everything. Then I did a clean re-install while trying to add WinXP to half of my drive (a nightmare but that's another story!).

Anyway, with the new install, my wireless chip (BCM4312 802.11b/g) isn't switching on at all. I've tried installing the Broadcom driver that appears when I run Hardware Drivers, but that doesn't help.

With the old install, the wireless switch and indicator light on the front of the netbook worked, now nothing.

Output from lshw -C network is:

 *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:55100000-55103fff

Output from nm-tool is:

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        00:23:5A:61:F5:B3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1
    DNS:             203.97.78.43
    DNS:             203.97.78.44

No sign of the wireless connection.

Any help would be greatly appreciated. I'm quite new to this whole Linux thing. ;)

Cheers.

---

### Post by Andyvanman on 2010-03-22
No one got any ideas?

---

### Post by bkratz on 2010-03-22
> **Andyvanman said:**
> No one got any ideas?

Which wireless driver did you install, the b43 or STA. Neither seems to show up in the above listing

How about posting 

lsmod
( LSMOD in lowercase) using the code tags (#)

---

### Post by Andyvanman on 2010-03-22
Hmmm, thats odd.

Last night when I was playing around with this, Hardware drivers was only offering me the b43 driver, no option to install the STA driver.

After reading your post bkratz I checked again and both drivers were available. I installed STA, wireless started working, computer froze, I rebooted and now its all fine.

I checked HArdware Drivers again and now only the STA is listed, not the b43 driver.

Thanks heaps. :D

---

### Post by bkratz on 2010-03-22
> **Andyvanman said:**
> Hmmm, thats odd.

Last night when I was playing around with this, Hardware drivers was only offering me the b43 driver, no option to install the STA driver.

After reading your post bkratz I checked again and both drivers were available. I installed STA, wireless started working, computer froze, I rebooted and now its all fine.

I checked HArdware Drivers again and now only the STA is listed, not the b43 driver.

Thanks heaps. :D


Well congratulations!  you solved your own problem. Please go to the thread tools and mark as [solved] in case it helps someone else.

---

