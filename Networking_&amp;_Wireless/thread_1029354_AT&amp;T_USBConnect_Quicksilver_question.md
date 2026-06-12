---
title: "AT&amp;T USBConnect Quicksilver question"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by n2iw on 2009-01-03
Hello All,

I must be missing something. I am reading all kinds of things on the internet telling about how easy and "out of the box" the AT&T USBConnect quicksilver is to get working in 8.10. But I can't find one that talks about how to actually accomplish it. 

I am not finding it very easy at all. As a matter of fact, I am finding it impossible. I have gotten it to work with something called HSO Connect from Pharlap. I do not want to use that program because it is way to buggy and it has crashed my system several times. 

My understanding is that Network Manager is supposed to be able to handle this swimmingly.

Can someone help. Or at least point me to a step by step procedure other than HSOConnect.

Thanks in advance,

System76 Darter, Ubuntu 8.10, AT&T USBConnect Quicksilver.

John

---

### Post by DonnieP on 2009-02-13
> **n2iw said:**
> I must be missing something. I am reading all kinds of things on the internet telling about how easy and "out of the box" the AT&T USBConnect quicksilver is to get working in 8.10. But I can't find one that talks about how to actually accomplish it. 

I am not finding it very easy at all. As a matter of fact, I am finding it impossible. I have gotten it to work with something called HSO Connect from Pharlap. I do not want to use that program because it is way to buggy and it has crashed my system several times. 

My understanding is that Network Manager is supposed to be able to handle this swimmingly.

You've probably found a solution by now, but I just got my Quicksilver yesterday.  I couldn't get it to work with HSOconnect or with network-manager.  But then just now I downloaded the hso.ko version 1.9 from the PHARscape forums.  Have to manually compile it and rename the stock hso.ko that comes with ubuntu 8.10, but it's simple to do and network-manager is now working.  Still can't get HSOconnect to work.  network-manager doesn't report any stats or even signal strength so I'd really prefer HSO until network-manager catches up.

---

