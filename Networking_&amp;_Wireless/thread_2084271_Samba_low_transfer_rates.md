---
title: "Samba low transfer rates"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by timZZ on 2012-11-14
Hi,

I have an issue in-which I have come to a cross roads in fixing.

I have two machines, 

1: 64 bit Ubuntu Machine running 12.10 - Atheros N-wireless adapter

2: 64 bit Windows 7 Machine - D-link N-wireless adapter

I cannot seem to achieve a higher speed than 2 Mbps.

What I have tried so far,

A: Gentoo box with Samba 3 is where this started

B: Switched from Gentoo to Ubuntu

C: Switched wireless routers

D: Attempted to play with the configuration to improve performance

I am literally staying stable between 1.8 Mbps - 2.0 Mbps

Where can I go from here?

To put it into perspective IF I run a test on speedtest.net I am apparently running an upload speed at almost 8Mbps - I can stream across the internet faster than local Samba shares.

---

### Post by BertN45 on 2012-11-14
If your samba shares are ntfs, then that is slowing down your transfers. I have the same type of speeds on ntfs on my wired network especially when writing to the ntfs samba share. Reading ntfs samba shares works faster. It is related to the current design of the ntfs support, which runs in user mode, which really slows things down. 

Ext3 or ext4 are at least 10 times faster.

---

### Post by timZZ on 2012-11-14
The computer with Samba installed is the ubuntu machine and it is writing to a ext 4 operating system.

Does that help?

---

### Post by BertN45 on 2012-11-15
How did you measure the transfer speed?

What is the speed if you copy a large file to the Windows machine?
What is the speed if you copy a large file to the UBUNTU machine?
What is the speed if you copy/paste a large file locally from a folder on the Ubuntu machine to your Samba share?

If it is a network problem, the first two should be almost the same. If it is a OS or file system issue, the last two might be close.

It does not really look like a network problem since your internet speed is 4 times higher, so the network seems fast enough.

By the way, it is not important that you have Ubuntu on an ext4 partition, but it is important where your Samba share is. Is that share on an ext4 or ntfs partition?

---

### Post by timZZ on 2012-11-15
FILE: Video
FILESIZE: 366 MB

[Samba] From Windows 7 to Ubuntu 12.10 - Transfer: 1.58Mbps
[Samba] From Ubuntu 12.10 to Windows 7 - Transfer: 1.66Mbps
[Scp through MobXTerm] From Windows 7 to Ubuntu 12.10 - Transfer: 2.4Mbps *Different Transfer Method*

OK not what I suspected

The share is on a ext4 file system. - Mount point is /media/samba

I have a mac and I will test from Windows to the Mac and from the Mac to Ubuntu.

---

### Post by timZZ on 2012-11-15
My equipment,

ROUTER: NETGEAR WNR3500L (Supports N-Dual)
WINDOWS 7: D-Link DWA-566 Wireless N 300 Dual Band PCIe
UBUNTU 12.10:  Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express)

For reference the the Atheros card is a single band N

---

### Post by timZZ on 2012-11-15
OK So I am attacking the usual suspects,

Ubuntu Drivers are up-to-date
Windows 7 had an update
Router had a firmware update

None of the above resulted in better performance.

According to the Network Settings (Not sure how accurate this is but I am getting use to the new interface of Unity) I am connected on the Ubuntu box @ 162 Mbps.
[B]
I will also move the Ubuntu box to the router and plug it in directly.  I will test to see if any performance advantage is giving by doing this.[/B]

---

### Post by BertN45 on 2012-11-15
I think the settings are reliable, I have seen them changing if I use my laptop far away from the router.
You could try forcing the router into G mode of 54 mbps. It would eliminate any potential compatibility problems in the N mode of working.
If the boxes are wired one by one as you intend, you could eliminate which of the boxes causes the problem.
You could also try swapping the cards, the other OS might treat that card better.
Switch off IPv6, might help.

---

### Post by BertN45 on 2012-11-15
Good idea to wire the boxes one by one. If that solves the problem, you could try in addition two other things.
- switch-off IPv6
- swap the cards, maybe the other OS has no problems with the card.

If nothing else helps try to force the router in G mode, it would eliminate all N incompatibility issues as a source of the problem.

---

### Post by timZZ on 2012-11-15
So I have moved the Ubuntu box onto Ethernet and I am now achieving between **5 - 6 Mbps**, which is a lot better than it was but I am still curious to where all the performance has gone.

I am going to try my Mac / Wife's Window 7 machine and see if there is a noticeable difference.

_My Windows 7 machine is claiming it is connected @ 240Mbps_

---

