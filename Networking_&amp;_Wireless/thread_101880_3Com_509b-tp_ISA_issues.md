---
title: "3Com 509b-tp ISA issues"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by René Kabis on 2005-12-10
I have an HP Pavilion 6532 with an Asus MEB-VM motherboard. The system is a Celeron 400 with 256Mb of memory. It has one ISA slot.

When I try two or three different ISA network cards (all of them 905B-TP models), the network cards are not recognized or even seen. Their status LED's (in the backplane, beside the socket) light up, so they are receiving power, but I am unable to get networking up and running. The hubs at the far end show no lights, indicating no connection. The Cat5 cable is fine. Both remaining slots (PCI only) are occupied, so I need ISA networking to work.

Any help would be appreciated.

---

### Post by az on 2005-12-10
ISA hardware cannot be safely probed by the kernel so it just does not do it.  You must load the module by hand

try

sudo modprobe 3c509

and see if that gives you an ethx.


If there are errors, it may be due to an irq conflict, which the kernel cannot configure because it is not pnp.  You would need to reserve the ird and port in your bios, as applicable.

---

### Post by René Kabis on 2005-12-10
[QUOTE=azz]ISA hardware cannot be safely probed by the kernel so it just does not do it.  You must load the module by hand

try

sudo modprobe 3c509

and see if that gives you an ethx.


If there are errors, it may be due to an irq conflict, which the kernel cannot configure because it is not pnp.  You would need to reserve the ird and port in your bios, as applicable.[/QUOTE]

Nothing happens at all. When I give that string in a terminal window, it simply refreshes the prompt without any response.

I am also testing out another ISA network card I found - EN2000 PNP, with a Realtek RTL8019AS chip. It also isn't recognized or even seen.

---

### Post by az on 2005-12-10
Actually, that is fine.  If the module loads fine, it does not show anything.  Load the module and check to see if it created an ethernet device for you by running
ifconfig

or run the networiking tool in your system administration menu and see if you can configure your network.

---

### Post by René Kabis on 2005-12-11
[QUOTE=azz]Actually, that is fine.  If the module loads fine, it does not show anything.  Load the module and check to see if it created an ethernet device for you by running
ifconfig

or run the networiking tool in your system administration menu and see if you can configure your network.[/QUOTE]

Sorry, the modprobe command doesn't make the 3com network card usable. When I try ifconfig, it doesn't show up, nor does it show up in my network setup.

Do you know the command to load the Realtek network card? If that doesn't work, I'll have to pull one of my PCI cards to install a PCI network card.

---

### Post by René Kabis on 2005-12-11
Actually, I had a brain fart. The 3com card is working now, but my only problem is that I have to re-do the card every time I reboot. Surely there is a string I can put into some config file that will load the card's drivers and activate the ethernet connection upon boot...

---

### Post by az on 2005-12-11
Yes.

Edit the /etc/modules file and add the name of the module to the end of the list.  all those modules get loaded on boot.


sudo gedit /etc/modules

---

### Post by René Kabis on 2005-12-11
And I found one of your comments exactly to that effect in another thread (ironically, also about the 509B cards...) and fixed it last night. Sorry I didn't point a link towards it, but I hit the sack immediately afterwards.

All in all, I'm finding Ubuntu to be a fine distro. Got some more questions, but that's for another thread in another category... I'm pretty well done with any networking problems right now. Thanks for all your help, Azz!

---

