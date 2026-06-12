---
title: "Why is my network interface suddenly called eth1_rename?"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by peterdm on 2010-09-04
Hi,

Today my network settings broke in Ubuntu. It still worked in recovery mode, so I knew it wasn't an infrastructural problem but a problem with the configuration somehow. Anyway, after booting in recovery mode (console with networking support), I got it working again, but for some reason 'eth1' has been renamed to 'eth1-rename'. I did not do anything special in the recovery console, just a ping to verify that the network worked.

When I do 'ifconfig -a', I now have

```

eth0
eth1_rename (!!!)
lo

```

Any idea how this could have happened?
And more importantly, how do I rename 'eth1_rename' back to 'eth1'?

As you can see, my PC has 2 network interfaces. It used to work with the cable plugged into either socket, but now it only works with the 'eth1_rename' socket. How do I get 'eth0' working again?

Peter

---

### Post by BkkBonanza on 2010-09-04
The naming is done during init by a udev rule. View it with,
**less /etc/udev/rules.d/70-persistent-net.rules**

Look in that file and you should see a few rules where it matches your MAC address to the name eth1_rename, and probably the past name as well. Make a backup of the file and then edit it so that it matches the MAC address and sets the name to eth1 as desired.

Usually udev will rename interfaces when the network card is changed and a new MAC address is detected. Once you correct this naming rule you can restart and it should get the right name.

---

### Post by peterdm on 2010-09-04
Hmmm... the udev rules still say 'eth0' and 'eth1', they don't mention 'eth1_rename'. Now, these are the 'persistent' rules, right? Is it possible that they are being overridden at startup with 'volatile' rules? Actually I have no idea, just thinking out loud here...

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4320 (skge)
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:18:f3:68:42:78", ATTR{type}=="1", NAME="eth0"

# PCI device 0x11ab:0x4364 (sky2)
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:18:f3:68:80:98", ATTR{type}=="1", NAME="eth1"

```

---

### Post by BkkBonanza on 2010-09-04
Hmmm. Googled a bit for you. There was a post out there that said that swapping the order of those rules fixed the problem for someone. Apparently some bug in udev. Don't know if that will work but it's worth a try.

I'd of thought it would be fixed by now though. Are you on a pretty old version of Ubuntu?

---

