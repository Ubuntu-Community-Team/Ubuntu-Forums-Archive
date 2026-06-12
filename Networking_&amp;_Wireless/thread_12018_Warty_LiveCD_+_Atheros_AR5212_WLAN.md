---
title: "Warty LiveCD + Atheros AR5212 WLAN"
date: 2005-01-21
forum: Networking &amp; Wireless
---

### Post by medicdave on 2005-01-21
Good morning!

I'm interested in using Ubuntu on my laptop, and I've just booted into the Warty livecd. Yesterday, in anticipation of today's experiments, I replaced my machine's built-in Broadcom WLAN card with an Atheros AR5212-chipset card. This way I don't have to mess around with ndiswrapper.

I've read in the wiki and forums that several folks with Atheros AR5212 chipsets have achieved "Just works" functionality. Unfortunately, I am not among them.

Doing a `lspci` indicates that my Atheros card has been enumerated on the PCI bus. But when I do a `iwconfig` or `sudo iwconfig`, I get no ath0. Figuring no modules are loaded, I check with `lsmod` or `sudo lsmod` and don't see "ath_pci" or "ath_hal" loaded.

Unfortunately, doing a `sudo modprobe ath_pci` or `sudo modprobe ath_hcl` tells me "FATAL: Module ath_pci not found." ... even though I can `cd /lib/modules/2.6.7/kernel/drivers/net && ls` and see both "ath_pci.ko" and "ath_hcl.ko" right there!

At this point, I'm a little lost. Anyone have any ideas?

Thanks,
medicdave

---

### Post by Philipude on 2005-06-19
My condulence
BROADCOM chipsets are to my knowledge seldom useable for Linux (see [http://linux_wless.passys.nl](http://linux_wless.passys.nl) or [http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List) ), while Atheros WLAN in general does support all. Though the longrange adapters like SMC in combination with Atheros are sometimes supported (yellow colour). Please give me some practical advice too, which names of adapters that also recieve perfect in longrange (not just chipsets).  :?

---

### Post by nanospire on 2005-09-23
I am having this exact same problem.  Please help, somebody...

---

