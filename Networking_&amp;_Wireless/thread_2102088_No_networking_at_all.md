---
title: "No networking at all"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by MarkW224 on 2013-01-06
Hi,

I've just installed Ubuntu 12.10 on a Desktop PC that was previously fully working under windows.  Ubuntu boots and I can log in but there is no networking at all.

I have tried all the following commands (using sudo)
```

lshw -C network
lspci 
ifconfig -a
dmesg

```And there is nothing at all there to do with networking or ethernet there, zilch.  

The motherboard is an ECS P4M890T-M v1.0 (VIA chipset).  Any ideas how I can get this to work?  There is no BIOS entry for disabling the network BTW.

---

### Post by MarkW224 on 2013-01-06
Solved: It was a BIOS problem fixed by clearing the BIOS.

---

### Post by Pjotr123 on 2013-01-06
Have you flashed the newest BIOS onto your motherboard? The "newest" BIOS for it, appears to fix a LAN issue:
[http://download.ecsusa.com/dlfileecs/bios/mb/p4/P4M890T-M/070808S.zip](http://download.ecsusa.com/dlfileecs/bios/mb/p4/P4M890T-M/070808S.zip)

Main download page:
[http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=671&CategoryID=1&MenuID=16&LanID=0](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=671&CategoryID=1&MenuID=16&LanID=0)

It just might help. And won't harm. :)

---

### Post by MarkW224 on 2013-01-06
Thanks, but it's working now.  IIRC you need a floppy drive the flash these mobos and I don't think I have any of these any more.

---

### Post by haqking on 2013-01-06
> **MarkW224 said:**
> Thanks, but it's working now.  IIRC you need a floppy drive the flash these mobos and I don't think I have any of these any more.

You havent needed floppies for this for some time.

[http://www.fdos.org/bootdisks/](http://www.fdos.org/bootdisks/)

[http://forums.mydigitallife.info/threads/1989-MS-DOS-7-10-LiveCD-BootCD-for-BIOS-Flashing](http://forums.mydigitallife.info/threads/1989-MS-DOS-7-10-LiveCD-BootCD-for-BIOS-Flashing)

[http://www.bootdisk.com/](http://www.bootdisk.com/)

And many more, Peace.

---

