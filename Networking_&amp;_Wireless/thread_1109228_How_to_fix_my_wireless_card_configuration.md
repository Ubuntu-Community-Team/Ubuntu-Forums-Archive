---
title: "How to fix my wireless card configuration??"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-28
I seemingly have successfully patched my wireless card with a driver that alows me to inject packets.

But in doing this I have lost all siganl too and from my card?

I cannot seem to enable my card. Or switch between managed and monitor mode?

I am still new to Ubuntu and would really appreciate I somebody would help me rectify this, but also give me instructions that a begginer/novice can understand?

I have lost all wireles connection whatsoever?

Wha can I do to fix this?

Here is the output from the  lspci -v command:
on the bottom line, you can see that The kernal modules have iwl3945 and ipwrar loading.

Is this what is causing the problem?

It was the iwl3945 driver i wanted to remove and replace with the ipwraw driver??
 

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1041
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at da000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipwraw	
        Kernel modules: iwl3945, ipwraw

I hope someodyb can help me sort this out, becuse it is beggining to bug me big time :)

---

### Post by chili555 on 2009-03-28
Please stay on one thread. We can't really hop between several threads trying to put the pieces together.

[http://ubuntuforums.org/showthread.php?t=1108643](http://ubuntuforums.org/showthread.php?t=1108643)

---

