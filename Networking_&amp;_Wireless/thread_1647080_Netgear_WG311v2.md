---
title: "Netgear WG311v2"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by memphiskane on 2010-12-16
[SIZE=3]Hey everybody,

I am seeking some help in regards to getting my wireless card to work.  I have used the sticky as well as read through the majority of the threads in this forum and many others to try and get this to work.  I am at my wits end as I was just trying out Ubuntu for the first time 10.04.  I ran:~$ dmesg | grep -e ndis -e wlan and below is what I came up with.  Any advice would be helpfull.

Thx,
Jim


[   14.135403] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.136574] ndiswrapper: driver wg311v2 (NETGEAR, Inc.,06/17/2004,6.0.5.30) loaded
[   15.137338] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 16 (level, high) -> IRQ 16
[   15.355284] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   15.355292] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   15.355305] ndiswrapper (mp_halt:262): device f00043a0 is not initialized - not halting
[   15.355309] ndiswrapper: device eth%d removed
[   15.355323] ndiswrapper 0000:01:06.0: PCI INT A disabled
[   15.355338] ndiswrapper: probe of 0000:01:06.0 failed with error -22
[   15.359591] usbcore: registered new interface driver ndiswrapper
[ 2048.363216] usbcore: deregistering interface driver ndiswrapper
[ 2048.365098] ndiswrapper (ntoskernel_exit:2677): object f0aa5120(2) was not freed, freeing it now
[ 2048.402986] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 2048.423124] ndiswrapper: driver wg311v2 (NETGEAR, Inc.,06/17/2004,6.0.5.30) loaded
[ 2048.423480] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 16 (level, high) -> IRQ 16
[ 2048.478272] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[ 2048.478282] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 2048.478296] ndiswrapper (mp_halt:262): device f0088ba0 is not initialized - not halting
[ 2048.478300] ndiswrapper: device eth%d removed
[ 2048.478322] ndiswrapper 0000:01:06.0: PCI INT A disabled
[ 2048.478345] ndiswrapper: probe of 0000:01:06.0 failed with error -22
[ 2048.480829] usbcore: registered new interface driver ndiswrapper[/SIZE]

---

### Post by memphiskane on 2010-12-17
Bump

---

### Post by dsdurkes on 2011-01-26
I have precisely the same issue. I had it working at one time but due to a crash, reloaded and have to start over at square 1 (or binary 0).

Any help out there?

---

### Post by JaySwartz on 2012-10-04
Looks like this doesn't happen often...but I too have the problem. I installed Precise 12.04 and the card won't work...any help this time around? Ran the same command and nothing comes up, so nothing was installed.

---

