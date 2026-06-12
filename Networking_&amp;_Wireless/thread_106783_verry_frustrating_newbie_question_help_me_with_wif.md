---
title: "verry frustrating newbie question: help me with wifi please!"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by shapiror on 2005-12-21
hey, i need some major help with this wifi crap.  i'm real new to linux, but i'm really trying to get used to it.  trying to learn a little... but i'm in a hole here.  i have a Proxim ORiNOCO IEEE 802.11a/b/g ComboCard Model: 8481-WD (pcmcia card).  how in the heck do i get this thing working?  it is my only way to get online, my ThinkPad 600 has no hardwire nic card.  i looked in the device manager and the card is being recognized, but it's showing up as an Atheros AR5212 802.11abg NIC and the bus type is PCI.

someone please help me through this.  i need someone to hold my hand on this one ;)  lol  but for real, please help me walk through this.

---

### Post by 23meg on 2005-12-21
I haven't done it myself, so I can't walk you through it, but I know you'll need to install and configure the madwifi drivers.

[http://sourceforge.net/projects/madwifi](http://sourceforge.net/projects/madwifi)

---

### Post by Lambert on 2005-12-21
Breezy includes a driver for pci devices with the atheros chipset.

All you should have to do is go to system>administration>networking 
Your card should show up in the list, highlight, click properties, ok and then try to activate.
If you card is not in the list then the driver is not working or loaded.

If your network is an open signal or wep with an open authentication (instead of shared/restricted) it should work. Any other network setting and some other configurations need to be done.

---

### Post by hajk on 2005-12-21
The madwifi driver for the OP's Atheros chip is in the linux-restricted-modules package for his kernel. He should install this package, since it is not installed in Breezy by default. 

I also recommend installing the network-manager package, which should take all the guess-work out of connecting to a wired or wireless network. Just stick the card into the PCMCIA slot and watch the the connection being made...

---

