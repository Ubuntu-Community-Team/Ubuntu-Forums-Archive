---
title: "Netgear WG511v2 problems"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by Freedomoffunk on 2006-06-14
Hi all, Im new to this Linux thing and have been having some problems with my wireless card.  I am using Ubuntu 5.10 and have installed my Netgear WG511v2 card using ndiswrapper.  So far so good! I can connect to my router fine and dandy and use the internet but yet after 2 mins of use the connection stops.  The power light still glows but the activity light either freezes on or off.  Removing & replacing the network card has no effect and ndiswrapper still shows the card as active.  Resetting the machine seems to be the only way to make it function again (and only for another 2 mins!)

I have six other windows/macs connected to the same router without problems so I know that it is something to do with my local machine.

Please help as I really dont want to be forced to go back to Microsoft madness!!

---

### Post by Freedomoffunk on 2006-06-14
bumpety bump!!!:D :D

---

### Post by Freedomoffunk on 2006-06-15
I take it that noone has any ideas then?:confused: :-(

---

### Post by honeydew on 2006-07-07
[http://www.ubuntuforums.org/showthread.php?t=185929&highlight=wg511v2](http://www.ubuntuforums.org/showthread.php?t=185929&highlight=wg511v2) 

dunno.. I recently purchased this card searching around for ideas.. I dont know how I feel about using ndiswrapper so Im thinking I might do a exchange.

good luck.

---

### Post by kc5hwb on 2006-07-08
I could never get my WG311 v2 PCI card to see my network with Ubuntu.  It worked fine when I had XP installed on the sam box, and Ubuntu even recognized it, but it never would see the network or the internet.  So I removed it and got another card.

---

### Post by kc5hwb on 2006-07-08
Netgear WG311 v2 PCI card
0000:00:03.0 0200: 1039:0900 (rev 90)

Airlink 101 USB
Bus 002 Device 002: ID 0ace:1215 ZyDAS


[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Listed at the top are the 2 wireless cards that I have tried, the first being the Netgear card.  In the link above, it shows all devices that are known to work with an ndiswrapper install.  This netgear card is listed in this list, but my chipset is not.

Has anyone else had this Netgear card working and if so, what is your chipset?

---

