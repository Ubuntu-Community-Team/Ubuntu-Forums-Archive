---
title: "Broadcom driver"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by ashish45d on 2013-06-28
My additional Wi-Fi broadcom driver not working after upgrading from 12.10 to 13.04. :(:(

---

### Post by rrich1974 on 2013-06-28
what kind of chipset?

---

### Post by Bucky Ball on 2013-06-28
Please run this in a terminal and post the output here:
```

sudo lshw -C network

```
Also, if you haven't already, get online with a cable, do an update and check 'Additional Drivers'.

---

### Post by splooroink on 2013-06-28
identical problem here (fine in 12.10, bad after 13.04 upgrade). don't want to hijack the thread, but my laptop has a bcm4313.

---

### Post by Bucky Ball on 2013-06-28
> **splooroink said:**
> don't want to hijack the thread ...

Then don't. ;)

Welcome to the forums. I advise you post a new thread with a descriptive title and as much information as you can think of about your issue (including the output from the command I posted earlier) in the ***Wireless & Networking*** sub-forum. Your problem *might* be identical but they rarely are and how could you know at this point? I very much doubt you have the same hardware config, even if the wireless cards are the same, and we have no idea about that yet as we haven't ascertained what the OP's is yet.

I would keep an eye on this thread for any clues an add anything you think might help OP. Helping two people on one thread is confusing, dilutes effort and is unfair to the OP. Good luck. ;)

---

### Post by Charlotte18 on 2013-06-29
I just had a similar problem with a Broadcom 4315  on a Dell M1330 laptop. The instructions on the following web site got the wireless working:

[https://help.ubuntu.com/community/BroadcomSTA(Wireless)](https://help.ubuntu.com/community/BroadcomSTA(Wireless))

---

