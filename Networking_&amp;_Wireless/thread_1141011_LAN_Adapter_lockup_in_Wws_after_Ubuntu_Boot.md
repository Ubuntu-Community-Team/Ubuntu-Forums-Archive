---
title: "LAN Adapter lockup in W****ws after Ubuntu Boot"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by GuitarGlen on 2009-04-28
OK - So sorry for mentioning the W*nd*ws word in this forum.
 
But I have installed Ubuntu 9.04 onto an existing Computer, which has an install of Windows XP.... And yes, I do need to leave it on there, as my kids will moan loudly when they cant access their games....:). FYI - Unbuntu runs well (fast too) - All good
 
Anyway, after installing Ubuntu, when booting up into windows, the Broadcom 10/100 LAN adapter can be seen, driver loads OK, however it reports "Media Disconnected". And, yes, if I rebooted into Ubuntu, the LAN worked just fine.
 
As part of the fault finding exercise, deleted the adapter, recreated it, tried all the IP reset and WINSOCK fixes that google could offer, but alas, no LAN in Windows, but LAN works in Ubuntu.
 
I used FIXMBR to remove the grub boot process, to determine if this was interfering with the windows operation, but this did not help.
 
Even though I had powered down the machine many times, in the end, I performed an actual physical Power-down of the computer (using the switch on the back of the power supply, not the 'soft' switch), alas, the Network Adapter springs back into life under windows.
 
So my immediate problem is fixed, however I thought I would perform some further diagnostic work, to confirm whether the Ubuntu install process 'broke' the adaper, or a normal startup/shutdown of Ubuntu. This confirmed that either will affect the adapter.
 
So the residual problem we seem to have is that UBUNTU 9.04 puts the LAN Controller into some nasty state, which requires a hard (physical)-power down, prior to starting windows. I have a work-around as per the above, but resolving this would be greatly appreciated.
 
Windows XP - SP3
Adapter - Broadcom 10/100 Integrated into ASUS A7V8X Motherboard
Latest BIOS from ASUS Support Site
LAN Driver was latest version from MS OS, but got downgraded to latest version from ASUS in the (panic) to fix this issue - Both had the same issue....
 
Thanks in advance.

---

### Post by tad1073 on 2009-04-28
same problem here with vista sp1

the other problem I am having is limited connectivity

I filled a bug report with launchpad yesterday and saw other bugs detailing what you have described.

---

