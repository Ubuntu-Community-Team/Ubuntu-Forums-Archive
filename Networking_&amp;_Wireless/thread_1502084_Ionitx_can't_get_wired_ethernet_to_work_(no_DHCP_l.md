---
title: "Ionitx can't get wired ethernet to work (no DHCP lease)"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by mageus on 2010-06-05
I have a Zotac Ionitx A-U.  I can't get it to establish an internet connection with the wired ethernet within Ubuntu.  The chip is detected, but trying to bring up the connection stalls out at trying to obtain a DHCP lease, like this:

DHCP DISCOVER ...
DHCP DISCOVER ...
No DHCPOFFERS received

Specs:
Ionitx A-U
Ubuntu 10.04 x64 kernel 2.6.32-22 (also didn't work in 9.10)

- hardware shows up in lspci (MCP79 ethernet)
- forcedeth module is loaded (lsmod)
- ifconfig shows the device as eth2 with correct MAC address, but no IP address assigned
- etc/network/interfaces - 
	auto eth2
	iface eth2 inet dhcp
- The wired ethernet works fine under Windows and another OS.
- Wifi works under Ubuntu and is autoconfigured
- This is not a MAC address reservation issue, as my router only does blacklisting on wireless addresses


Any ideas how to troubleshoot further?

TIA.

---

### Post by project23 on 2010-06-07
This may sound crazy, but try a cold reboot. Actually turn off the system and unplug it from the AC power. This will allow the hardware to fully power down and perform a hardware level initialization when you reapply power.  

I just spent 2 days mucking around with my new netbook (HP mini 311) which uses the same ION chipset. The wired ethernet worked great under windows 7 (the preinstalled OS), but refused to hear a valid DHCP response after I installed Gentoo. Unplugging the system and removing the battery allowed the hardware to be truly powered down. Now the wired ethernet works as expected.

---

### Post by mageus on 2010-06-07
Yes, I was thinking about this.

I remember, *years* ago, this used to be a problem on certain ISA and PCI add-in cards.  Something about Windoze writing to the device's EEPROM, rendering it unusable to another OS on the next boot.

I'll give it a shot.

---

### Post by mageus on 2010-06-10
Yep, that was it.  's a pain to pull the plug every time I want to dual boot.

Another thing:
I get weird network performance when both wifi and wired enet are active.  Lots of intermittent dropout in bandwidth.  Things work fine if I disable wireless.  I guess this makes sense, but I've never noticed such behaviour on my laptops.

---

### Post by jerkfaceirl on 2011-11-13
Thanks for telling me to power down the system, had exact same problem and it fixed it, latest ubuntu.

---

