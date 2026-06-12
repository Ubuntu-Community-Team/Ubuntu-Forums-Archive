---
title: "Wired works, wireless gets nothing"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by yipyip123 on 2011-03-11
So, I used to have the opposite problem.

Right now, only wired internet works on my lucid lynx partition, while both wired and wireless work on my windows partition. It just doesn't seem to detect any wireless sources. My wireless is not off. I'm not sure how to solve this problem. How do I begin to diagnose my problem?? 



Thank you

---

### Post by Rob_H on 2011-03-11
> **yipyip123 said:**
> So, I used to have the opposite problem.

Right now, only wired internet works on my lucid lynx partition, while both wired and wireless work on my windows partition. It just doesn't seem to detect any wireless sources. My wireless is not off. I'm not sure how to solve this problem. How do I begin to diagnose my problem?? 



Thank you

Begin by posting the output of the **lspci** command. That will help identify your network hardware and start you on the road to getting the correct driver.

---

### Post by Rob_H on 2011-03-11
Even better, post the result of:

```
sudo lspci -v
```

You only need to include the section that talks about your wireless device, though. We don't need your entire hardware inventory. :)

---

### Post by kc1di on 2011-03-11
Hi,
it would help to know what the wireless card is in your machine.

If it is a card that needs extra drivers or firmware like mine does you may be able to get them by going to system>administration>Hardware Drivers.

---

### Post by yipyip123 on 2011-03-11
Well apparently my ubuntu's wireless is working now, at home (spring break), but didn't work at college?

This was true after winter break as well. But wireless worked fine in both locations prior to that.

is this the code?

```
 
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Device 1a3b:1067
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

---

### Post by Rob_H on 2011-03-11
Yup, that's it. Hmmm.. once upon a time, Atheros chipsets required [Madwifi]("http://madwifi.org/") drivers, but my info might be several years out of date or maybe those drivers ship with Ubuntu now.

In any case, it sounds like the problem is environmental since it is working now. Next time it stops working, try running

```
sudo iwlist scan
```

to see if you're picking up any wireless access points at all.

---

