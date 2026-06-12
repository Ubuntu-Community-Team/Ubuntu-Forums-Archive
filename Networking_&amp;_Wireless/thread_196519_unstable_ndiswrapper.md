---
title: "unstable ndiswrapper"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by mpeng on 2006-06-14
Hi, 

Why my ndiswrapper can not run for a long time. After running a while, it got errors, the "dmesg | grep ndiswrapper" shows the following information. Who can help me out?

[4304515.755000] ndiswrapper version 1.17 loaded (preempt=yes,smp=no)
[4304515.874000] ndiswrapper: driver sis162u (Silicon Integrated Systems Corp.(1.03.09),07/28/2004,5.1.1039.1030) loaded
[4304521.621000] w[4304515.755000] ndiswrapper version 1.17 loaded (preempt=yes,smp=no)
[4304515.874000] ndiswrapper: driver sis162u (Silicon Integrated Systems Corp.(1.03.09),07/28/2004,5.1.1039.1030) loaded
[4304521.621000] wlan0: ndiswrapper ethernet device 00:0a:eb:88:6a:db using driver sis162u, 0B3B:1613.F.conf
[4304521.776000] usbcore: registered new driver ndiswrapper
[4304720.128000]  [<d0c5e6a7>] wrap_alloc_urb+0xe7/0x290 [ndiswrapper]
[4304720.128000]  [<d0c5ec10>] wrap_bulk_or_intr_trans+0x60/0x1b0 [ndiswrapper]
[4304720.128000]  [<d0c5f769>] wrap_submit_irp+0xc9/0xd0 [ndiswrapper]
[4304720.128000]  [<d0c59551>] pdoDispatchDeviceControl+0x11/0x30 [ndiswrapper]
[4304720.128000]  [<d0c578b9>] IofCallDriver+0x29/0x50 [ndiswrapper]
[4304720.128000]  [<d0c579bd>] IofCompleteRequest+0xdd/0x190 [ndiswrapper]
[4304720.128000]  [<d0c5e9fd>] wrap_urb_complete_worker+0x7d/0x170 [ndiswrapper]
[4304720.130000] ndiswrapper (wrap_alloc_urb:383): couldn't allocate dma buf
[4304720.130000] ndiswrapper (wrap_bulk_or_intr_trans:660): couldn't allocate urb
lan0: ndiswrapper ethernet device 00:0a:eb:88:6a:db using driver sis162u, 0B3B:1613.F.conf
[4304521.776000] usbcore: registered new driver ndiswrapper
[4304720.128000]  [<d0c5e6a7>] wrap_alloc_urb+0xe7/0x290 [ndiswrapper]
[4304720.128000]  [<d0c5ec10>] wrap_bulk_or_intr_trans+0x60/0x1b0 [ndiswrapper]
[4304720.128000]  [<d0c5f769>] wrap_submit_irp+0xc9/0xd0 [ndiswrapper]
[4304720.128000]  [<d0c59551>] pdoDispatchDeviceControl+0x11/0x30 [ndiswrapper]
[4304720.128000]  [<d0c578b9>] IofCallDriver+0x29/0x50 [ndiswrapper]
[4304720.128000]  [<d0c579bd>] IofCompleteRequest+0xdd/0x190 [ndiswrapper]
[4304720.128000]  [<d0c5e9fd>] wrap_urb_complete_worker+0x7d/0x170 [ndiswrapper]
[4304720.130000] ndiswrapper (wrap_alloc_urb:383): couldn't allocate dma buf
[4304720.130000] ndiswrapper (wrap_bulk_or_intr_trans:660): couldn't allocate urb

Thanks.

---

### Post by pelle.k on 2006-06-14
This is not ndiswrapper 1.8, which is in dapper, so i guess you built it yourself right? No errors when building?
Also, ndispwrapper is REALLY picky about what version of a windows driver you are using. Try diffrent versions.

---

### Post by mpeng on 2006-06-14
Yes. I compiled and installed the ndiswrapper successfully. The driver is from XP driver. The same driver works well in Ubuntu 5.10.  I have tried the driver from WIN2000 also, it does not help.  thanks.

---

### Post by pelle.k on 2006-06-15
OK. What i meant was that driver revision, or version number is what's important. Like 1.89 / 2.48... you get the picture right? I had to try three versions of the same driver just to get it to respond att all using ndiswrapper...

---

### Post by noname101 on 2006-06-15
Since you said it works fine in ubuntu 5.10. Maybe if you use whatever version of ndiswrapper you were using then.

---

