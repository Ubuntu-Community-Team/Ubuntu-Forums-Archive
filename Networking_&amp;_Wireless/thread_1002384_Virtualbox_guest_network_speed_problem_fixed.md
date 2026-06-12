---
title: "Virtualbox guest network speed problem fixed"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by ryecomp on 2008-12-04
Configuration : 

virtualbox 1.5.6
host : ubuntu 8.04
guest : windows 2000 prof
internet line : 100Mbps
nic : RTL8139 compatibles

Problem : 

1) samba shared folder access in guest OS extremely slow 
2) upload network performance in guest OS too slow 
   (download is 72Mbps, but upload is 2Mbps)

When tested in test site ([www.bechbee.co.kr](www.bechbee.co.kr)), I got a packet loss 
of 87% when service average is 0.17% ... !!!

Tried : 

1) Changing nic in virtual box setting screen. But best of 3 nic's 
selectable in virtualbox is AM79C973, which was already used. 

2) Changing NAT interface to Host interface. It slow down download
performance to 52Mbps, but upload performance is back to 70Mbps and 
packet loss to 0%. 

Result : 

Changing NAT->Host interface affect download performance to 72% but 
upload performance/packet loss can be greatly improved. This change 
also let you enter samba shared directory instantly. ):P

---

### Post by JPWhite on 2010-02-10
Using the default NAT network adapter resulted in extremely unsatisfactory performance.

Switched to the bridged adapter and got full network speed both download and upload, achieving 6MBs up and down :P.

VB 3.1.2
Ubuntu 9.10 32-bit guest
Win XP SP3 Host with Broadcom Gigabit wired NIC.

---

### Post by pwebster25 on 2010-03-21
> **JPWhite said:**
> Using the default NAT network adapter resulted in extremely unsatisfactory performance.

Switched to the bridged adapter and got full network speed both download and upload, achieving 6MBs up and down :P.

VB 3.1.2
Ubuntu 9.10 32-bit guest
Win XP SP3 Host with Broadcom Gigabit wired NIC.

This seemed to solve my problem too, with the opposite setup.  I tried everything else first, as NAT is the default.

I am on VB 3.1.4 and Ubuntu 9.10 32Bit (Host)
WinXP Sp3 is the Guest

---

### Post by thelastbiscuitinthetin on 2011-11-19
> **JPWhite said:**
> Using the default NAT network adapter resulted in extremely unsatisfactory performance.

Switched to the bridged adapter and got full network speed both download and upload, achieving 6MBs up and down :P.

VB 3.1.2
Ubuntu 9.10 32-bit guest
Win XP SP3 Host with Broadcom Gigabit wired NIC.

This worked for me. I just changed it from NAT to Bridged Adapter and hit OK.

---

### Post by statikeffeck on 2011-11-19
:lolflag: I wish I had seen this topic before going through a couple hundred uploads of music MP3s through my Windows 7 guest OS.  I thought it was just my internet connection! It must have taken 4 times as long due to the bug.

I will have to try switching the adapter type to Host.

---

