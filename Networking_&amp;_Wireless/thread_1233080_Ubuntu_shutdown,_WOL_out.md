---
title: "Ubuntu shutdown, WOL out"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by ndhert on 2009-08-06
Ubuntu 9.04 on PC with network card (from lspci | grep Eth)
Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
 
When shut down, the light on the netwerk card goes out and stays out.
Sending a wake-on-lan (WOL) signal does not start up the system.
 
PC is dual boot WinXP/Ubuntu, when shut down from WinXP, the light
of the network card stays on, sending a WOL starts the system.
(the PC is BIOS-configured for WOL)
 
When (after Ubuntu shutdown) pulling out the power cable for a minute, then
plugging-in, the light on the network card comes up and WOL is 
possible. But this solution is no option for me. I need WOL to be 
possible after Ubuntu shutdown without manual intervention.
How to remedy?

---

