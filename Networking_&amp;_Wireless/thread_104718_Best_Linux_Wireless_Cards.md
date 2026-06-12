---
title: "Best Linux Wireless Cards?"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by neolev on 2005-12-16
Can anyone list any of the retail store brand wireless cards that are ready to roll with unbuntu??

Need a wireless setup and i gave up on my WPN111 doesnt seem to have support for it....wanna go PCI....with something that ubuntu supports and not waste time so any help would be appreciated...


Neolev

---

### Post by arpunk on 2005-12-16
[QUOTE=neolev]Can anyone list any of the retail store brand wireless cards that are ready to roll with unbuntu??

Need a wireless setup and i gave up on my WPN111 doesnt seem to have support for it....wanna go PCI....with something that ubuntu supports and not waste time so any help would be appreciated...


Neolev[/QUOTE]
Theres been a few threads on this, you should search for them... long story short, any atheros based card is well suported in linux.

[http://customerproducts.atheros.com/](http://customerproducts.atheros.com/)

---

### Post by neolev on 2005-12-16
[QUOTE=arpunk]Theres been a few threads on this, you should search for them... long story short, any atheros based card is well suported in linux.

[http://customerproducts.atheros.com/](http://customerproducts.atheros.com/)[/QUOTE]

Currently have a Netgear WPN111 USB (atheros chipset) and i cant get it the correct driver and it doesnt seem to have support in nix

Neolev

---

### Post by SteelValor on 2005-12-16
got english? ;D

---

### Post by arpunk on 2005-12-16
[QUOTE=neolev]Currently have a Netgear WPN111 USB (atheros chipset) and i cant get it the correct driver and it doesnt seem to have support in nix

Neolev[/QUOTE]
[http://atheros.rapla.net/](http://atheros.rapla.net/)

Weird, your card isnt listed there and ill check again when the atheros customer page is working, probably your card *isnt* an atheros based one?

If your card is indeed atheros based, then try the *madwifi* drivers which are in the *linux-restricted-modules-(your kernel version)*.

---

### Post by neolev on 2005-12-16
Tried to set it up via ndiswrapper and madwifi no luck either way....ndiswrapper 1.7 shows 

Card: Netgear WPN111 108Mbps RangeMAX USB (with super G/MIMO)
Chipset: Atheros USB
pciid: 1358:5f01
Driver: Windows XP driver available on the Netgear CD: netwpn11.inf + wpn111.sys + ar5523.bin
Other:Works with latest cvs 1.6(29/11/05) you must run 'load_fw_ar5523 /etc/ndiswrapper/netwpn11/ar5523.bin' before running modprobe

But even now it doesnt work

---

### Post by sarah_b on 2005-12-17
I highly recommend these:

Linksys EtherFast PCI Adapter LNE100TX
Linksys Wireless PCI Adapter WMP54G

---

### Post by Lambert on 2005-12-17
d-link dwl-g650 revision b5 worked for me.

not sure where you're at but best buy for $30 (after $20 mail in rebate)

---

