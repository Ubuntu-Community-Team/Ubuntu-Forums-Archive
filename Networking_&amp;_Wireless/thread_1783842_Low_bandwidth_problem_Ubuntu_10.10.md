---
title: "Low bandwidth problem Ubuntu 10.10"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by nelson_drake on 2011-06-16
Greetings!

I've been struggling with this problem for a week now. I've searched and tried tons of 'fixes'. So far nothing has worked.

For some reason, I seem to be stuck at 160k. The only change was a physical move. Same cable internet that speed tests at 1.44mbps down.

I've disabled IPv6 and tried many different suggestions as I've seen many posts on this issue, but nothing works. I have Windows7 dual boot on the same machine and it is fine. 750-900k down easy.

This happens wired or wireless as well. I'm at my wits end. I'm going to see if it happens on an ubuntu live cd...

Can anyone make a suggestion?

---

### Post by nelson_drake on 2011-06-16
Just to add more detail... I've done some further testing. And I don't think this is an Ubuntu problem... I'll break it down in bullet points.

My downloads come from half a dozen sites that I know in the past have given me 400kb to 600kb. I've also tested with torrents that I know come in fast, ie: Ubuntu disc images which and others.

- My bandwidth appears to be capped at 175kb while speed tests from multiple sites show me at 1.44mbps
- Brand new cablemodem and Cisco (Linksys) Router
- Doesn't matter, wired or wireless
- Tested with Fedora15 LiveCD and Windows7 Live CD... never got above 175k.
- If downloading, and maxed out at 175k, Vonage is not usable. So this eliminates the computer/NIC aspect.

Same box routinely got over 1mbps down. It looks like the issue is with Comcast cable, however that doesn't explain my speed test results.

If anyone has any ideas, I'd love to hear them...

---

### Post by StrayEddy on 2011-06-16
The problem could be related to your connection devices **drivers**.

Did you get the latest drivers for them:

Open a terminal (Ctrl+Alt+T) and type:

lspci

Post the result please

---

### Post by nelson_drake on 2011-06-16
The thing that throws me is Vonage... it's connected directly to the router. The only way I can make a call is if I pause all downloads.

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Thanks!

---

### Post by nelson_drake on 2011-06-16
A bit more detail...

  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:82:4e:a7:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: e0:cb:4e:40:00:41
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.117 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:e800(size=256) memory:feaff000-feafffff memory:fdffc000-fdffffff memory:feac0000-feadffff

---

### Post by StrayEddy on 2011-06-16
This could help your **wireless **problem maybe:

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

And this for your **ethernet **problem:

[http://ubuntuforums.org/showthread.php?t=723569](http://ubuntuforums.org/showthread.php?t=723569)

---

### Post by nelson_drake on 2011-06-16
Ok... I'll check it out. I'm also going to look at a firmware upgrade for the router.

Thanks!

---

### Post by nelson_drake on 2011-06-17
Just to update this thread... there is no solution so far. I've tried everything suggested above, no change.

I've been on the phone with Comcast cable and had a tech out to check the line... no change. Speed tests still show me at 1.44mbps, but I'm capped at 175k down.

I ever had a linux guy I've known for ages help. He's an admin for a company in NYC. He remoted in and spent 2 hours looking around and is still scratching his head.

At this point, I'm opting to buying a new computer. I doubt changing the NIC will help, but at least it's a cheaper option.

Thanks again for all the help!

---

