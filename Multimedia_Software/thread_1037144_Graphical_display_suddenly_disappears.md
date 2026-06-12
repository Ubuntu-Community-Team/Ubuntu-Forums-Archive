---
title: "Graphical display suddenly disappears"
date: 2009-01-11
forum: Multimedia Software
---

### Post by lesliek on 2009-01-11
I'm using v 8.10 and I have all offered updates installed. Once yesterday and once today, the above happened to me, though it's never happened before.

I understand little of these things, but I found this in /var/log/daemon.log:

Jan 12 05:41:30 leslie-desktop gdm[5385]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

I assume that that was today's crucial moment.

Could that be related to a recent software update?

I'd appreciate any guidance.

Thanks for reading this.

Leslie

Edit: in the file called /var/log/gdm/:0.log.1, I found:

"Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x00000001 getbl_err: 0x00000000
ipeir: 0x00000000 iphdr: 0x54f00006
LP ring tail: 0x000001b0 head: 0x0001f674 len: 0x0001f001 start 0x00000000
eir: 0x0000 esr: 0x0001 emr: 0xffff
instdone: 0xfa41 instpm: 0x0000
memmode: 0x00000306 instps: 0x80007826
hwstam: 0xfffe ier: 0x0002 imr: 0x0000 iir: 0x00c0
Ring at virtual 0xa78a1000 head 0x1f674 tail 0x1b0 count 719
[repeated many, many times]
Ring end
space: 128188 wanted 131064

Fatal server error:
lockup

Error in I830WaitLpRing(), timeout for 2 seconds"

I have no idea what it means, but I assume that it's my problem.

---

