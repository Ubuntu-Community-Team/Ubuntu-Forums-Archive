---
title: "Netgear WG111"
date: 2005-02-22
forum: Networking &amp; Wireless
---

### Post by Joe on 2005-02-22
Has anyone been able to get a Netgear WG111 wireless adapter to work in Warty?  I'm trying to get it working using ndiswrapper but have been unsuccessful.  I keep getting this error when I run "modprobe ndiswrapper."

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by yatesco on 2005-02-23
Have you done the ndiswrapper -i <driver.inf> first?

What does ndiswrapper -l show?

If you don't have any drivers loaded in ndis, then indeed modprobe ndiswrapper will fail.

---

### Post by Joe on 2005-02-23
[QUOTE=yatesco]Have you done the ndiswrapper -i <driver.inf> first?

What does ndiswrapper -l show?

If you don't have any drivers loaded in ndis, then indeed modprobe ndiswrapper will fail.[/QUOTE]
 Yes I did the ndiswrapper -i and ndiswrapper -l and it detects both the driver and the hardware.

---

### Post by phxguy on 2005-03-23
Joe,

Did you Ever Get This Working? I also have a  Netgear WG111 and it is not being seen at all. Where do I get the driver for it?

---

### Post by Mr Black on 2005-03-23
Joe,

The reason why the modprobe command is failing is because you need to be root in order to run it.  Try running it like this...

*sudo modprobe ndiswrapper*

The system will then prompt you for the password.

---

