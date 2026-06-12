---
title: "ethernet device changes number on each boot"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by democritus74 on 2009-12-28
My ethernet device changes its name on each reboot of the computer, or using "/etc/init.d/networking restart".

I am running Ubuntu Studio 9.10 32 version.  My LAN card is built into the motherboard, an nVidia MCP55 Ethernet (revision a2)

Can someone please help me to stop this behaviour?  I'd expect my ethernet device to appear as eth0 all the time.

---

### Post by Iowan on 2009-12-28
Does it always increase - or is it random? There were a couple of threads where eth# kept increasing. One cure was to edit */etc/udev/rules.d/70-persistent-net.rules * and remove the extra definitions.

---

### Post by democritus74 on 2009-12-28
> **Iowan said:**
> Does it always increase - or is it random? There were a couple of threads where eth# kept increasing. One cure was to edit */etc/udev/rules.d/70-persistent-net.rules * and remove the extra definitions.
Thanks for the reply.

The eth# always increases by 1 each time.  Your reply allowed me to look up other posts on this issue thanks to the file "70-persistent-net.rules".

The solution I have gone with for now is to empty the "70-persistent-net.rules" file except for eth0 entry, then copy the file /lib/udev/rules.d/75-persistent-net-generator.rules to /etc/udev/rules.d/75-persistent-net-generator.rules.  In the /etc/udev/rules.d copy of the file I removed "eth*" from the line:
KERNEL!="eth*|ath*|wlan*[0-9]|msh*|ra*|sta*|ctc*|lcs*|hsi*", GOTO="persistent_net_generator_end"

So it now appears as:
KERNEL!="ath*|wlan*[0-9]|msh*|ra*|sta*|ctc*|lcs*|hsi*", GOTO="persistent_net_generator_end"


I don't know if this is the best approach to fixing the problem, but is does solve the problem for me.  Multiple reboots and my network interface stays as eth0.


Thanks for the help :)

---

