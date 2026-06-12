---
title: "Compaq CQ50-115NR Wireless Not Working (Atheros)"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by eperry2011 on 2009-11-04
Hi!  I've tried upgrading to Ubuntu 9.10 and the wireless card is not working in my laptop.  I have been using Ubuntu up to 9.10 release candidate, but I decided to fresh install the system (to see the new GRUB), and everything worked flawlessly...except for the wireless - it is an Atheros AR2--- card that was working fine with Ubuntu 9.04 (which I am using right now because it's what works - and I've got to have wireless working for school)...help?

(info from Ubuntu 9.04)
lspci -v | less
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath_pci, ath5k


Why would it STOP working?  Why mess with something that ain't broke? lol...any help would be greatly appreciated - thanks! :D

---

### Post by eperry2011 on 2009-11-04
It says that the wireless is disabled at the top of the screen, and when I look at other places on the forum, they talk about

"#" blacklist ath5k

...but my blacklist-ath_pci.conf file doesn't have that line - it's blacklisting ath_pci...if that's of any help...(I've put 9.10 back on it...ugghhh...)

---

### Post by eperry2011 on 2009-11-06
Doesn't anyone have anything to help? gosh...guess I'll stay with 9.04 or try some other distro...

---

### Post by Capzoots on 2011-09-15
So 9.04 works cause I'm having this same problem with 11.04 too bad too I was almost a new convert.

---

