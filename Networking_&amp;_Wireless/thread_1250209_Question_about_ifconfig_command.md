---
title: "Question about ifconfig command"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by Riddermark on 2009-08-26
I wanted to check if eth0 is in promiscuous mode or not.  Is the ifconfig command suitable for determining this?  If eth0 is in promiscuous mode, promisc should be in the output,...correct?

Thanks

K

---

### Post by compiledkernel on 2009-08-26
Simply put, to put the interface in promiscuous is quite like this -- 

sudo ifconfig <iface> promisc 

Generally speaking unless an application tries to dump your interface into promiscuous mode, it is traditionally NOT in promisc by default.

---

### Post by Riddermark on 2009-08-26
> Simply put, to put the interface in promiscuous is quite like this -- 

sudo ifconfig <iface> promisc 

Generally speaking unless an application tries to dump your interface into promiscuous mode, it is traditionally NOT in promisc by default.I agree about the default setting being -promisc.  I recently ran an app and just wanted to check and make sure that I have not changed to promisc mode inadvertently.  I just wanted to know the best way to check and see what the status of the interface is, just to be sure.


Thanks

K

---

### Post by aesis05401 on 2009-08-26
> **Riddermark said:**
> I agree about the default setting being -promisc.  I recently ran an app and just wanted to check and make sure that I have not changed to promisc mode inadvertently.  I just wanted to know the best way to check and see what the status of the interface is, just to be sure.


Thanks

K

Yes, it will appear in ifconfig output in the line with the other flags.  Here is a line from my current eth0:

UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1

---

