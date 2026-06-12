---
title: "AR928X wireless problems"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by andrewpmk on 2009-10-31
Hi, my AR928X wireless card on a Toshiba Satellite M800 is working erratically since I upgraded to Ubuntu 9.10. It will often randomly stop working for no apparent reason, often after only a few minutes of being connected (it varies quite a bit). It seemed to work fine in Ubuntu 9.04.

Here is output of lspci -v:

08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Askey Computer Corp. Device 7141
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at c0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: ath9k
        Kernel modules: ath9k

---

### Post by nomes on 2009-11-01
im having the same problem but on a gateway lt110. Mine seems to go down when i go into standby or hibernation.  The Actual wireless connection does not go down but it does not seem to resolve host names...

---

### Post by mattweed9 on 2009-11-01
Hi, Andrew.

I had the same exact problem. I have found  that using another network manager fixed the issue. I used Wicd which you can find in the software manager. I installed it and rebooted, since then I haven't had any problems.

This isn't a sure fix, but it worked for me and I was having the exact problem. It doesn't seem to improve signal strength, but it is fairly good. Better at least then losing connecting all the time.

Hope this help[s you.

---

### Post by nomes on 2009-11-13
its a little better, but still hibernation and suspend is an issue.....now with Wicd its sometimes works and other times u still have to reboot when u resume.....

---

### Post by diogobaeder on 2009-11-15
I've had the exactly same problem, and also with Jaunty.

Now I installed wicd, but it just can't find any connection. Going back to NM, because at least it works sometimes.

Diogo

---

