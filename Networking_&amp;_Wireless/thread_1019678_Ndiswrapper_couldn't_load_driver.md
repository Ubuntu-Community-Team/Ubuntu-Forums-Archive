---
title: "Ndiswrapper couldn't load driver"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by toolfan202 on 2008-12-23
I am dual booting Ubuntu 8.04 with Vista x64 on my new laptop.  Specs are: 2.4Ghz Intel dual core, (2) ATI 3780m CrossfireX GPUs, 4 Gigs 1066 ram, Intel 5300 wireless b/g/n adapter.  

My problem is I can't get Ndiswrapper to load the driver for the wireless adapter.  I have tried both Windows XP and Vista versions with no success, I keep getting the same feedback.

Here are the results of: dmesg | grep -e ndis -e wlan

[ 193.280645] usbcore: registered new interface driver ndiswrapper
[ 220.929053] usbcore: deregistering interface driver ndiswrapper
[ 220.929917] ndiswrapper (ntoskernel_exit:270: object ffff81013a379630(2) was not freed, freeing it now
[ 220.943686] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 220.962985] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[ 220.963126] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x64'
[ 220.963955] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x64; check system log for messages from 'loadndisdriver'
[ 220.967772] usbcore: registered new interface driver ndiswrapper

And the results of: ~lshw -C Network  shows the first wired ethernet adapter, which is blacklisted, and the wireless adapter which I need to be working.

*-network UNCLAIMED
description: Ethernet controller
product: 88E8055 PCI-E Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:08:00.0
version: 12
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
*-network UNCLAIMED
description: Network controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:09:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0

Please can someone help?  I don't know what to do now.

---

### Post by ieee488 on 2008-12-23
Vista drivers won't work with ndiswrapper.

---

### Post by toolfan202 on 2008-12-24
I realized that, so I tried XP drivers with no success.

---

### Post by S_e_P_p on 2008-12-24
I can't remember exactly but I think there wasn problem with root or something like that.

So you have to open an terminal and start ndiswrapper with sudo..

I think it was something like: sudo ndisgtk

But not sure about that.

Greets,
SePp

---

### Post by masterpop on 2009-03-08
hi,
I have exactly the same issue. Were you able to solve it?

Thanks for any tips,
Alex

---

### Post by TSJason on 2009-05-24
Ditto - Same issue here.

---

