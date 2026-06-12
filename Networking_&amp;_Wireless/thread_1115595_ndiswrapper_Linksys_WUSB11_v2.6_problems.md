---
title: "ndiswrapper Linksys WUSB11 v2.6 problems"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by calvinthewikipedian on 2009-04-04
I just set up a dual boot (Vista - Ubuntu). The wireless adapter I use is a Linksys WUSB11 V2.6 802.11b adapter. I tried to use ndiswrapper to use the default Linksys driver, but it doesn't work. The only problem I found was when I ran this:
> 
dmesg | grep -e ndis -e wlan

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper: driver netusb (Linksys,11/12/2001,2.10.37.2037 loaded
ndiswrapper (mp_init:219): couldn't initialize device: C0000001
ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
ndiswrapper (mp_halt:262): device f7b6b480 is not initialized - not halting
ndiswrapper: device eth%d removed
Modules linked in [...removed for clarity...]
  [<f8c8d563>] ? ntdriver_thread+0x73/0xb0 [ndiswrapper]
  [<f8c8d4f0>] ? ntdriver_thread+0x0/0xb0 [ndiswrapper]
BUG: unable to handle kernel <4>ndiswrapper: probe of 5-1:1.0 failed with error -22


Could this be the problem? If so, how do I fix it? Does anyone know a good way to get the Linksys WUSB11 V2.6 802.11b adapter to work in Ubuntu?

---

