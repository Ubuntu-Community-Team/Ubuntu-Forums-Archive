---
title: "eth0: transmit timed out -- workaround"
date: 2006-04-04
forum: Networking &amp; Wireless
---

### Post by johnpipe on 2006-04-04
Hi,  I had trouble after an upgrade, due to wrong answers to the prompts on boot block and lilo. So, I had ended up with breezy after upgrade from hoary,  but with still the hoary 2.6.10 kernel.

The next time I booted, having not remembered to update lilo on the actual boot partition ( RH6.1 on a 233mmx, on hda1, ubuntu is on hdb9), I got the hoary kernel, and good thing, because there was no breezy kernel then installed.

With the wrong kernel installed, the hotplug system disabled the IRQ 10, which is used by eth0, so no access to the network, and many error messages such as:

Mar 30 17:21:02 localhost kernel: irq 10: nobody cared (try booting with the "irqpoll" option.

Mar 30 18:22:27 localhost kernel: NETDEV WATCHDOG: eth0: transmit timed out
Mar 30 18:23:27 localhost last message repeated 4 times

(there were a LOT more error messages than this small selection)

This behavior was because a kernel bug in 2.6-10 and earlier, according to searches results from debian lists.

The suggestion in the message worked, I'm connecting from ubuntu now. I entered the following in lilo.conf on the RH (boot default) partition, at the end of the ubuntu section:

     append:irqpoll

This got the network card up and the network working again.  I used synaptic to get a new kernel, though for some reason the default breezy kernel doesn't appear in the base repositories, so I had to go for 2.6.12-9; hope it works! It's one lower than the latest shown in the base repository and higher than breezy default.

HTH, johnpipe

---

