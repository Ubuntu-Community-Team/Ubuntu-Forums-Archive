---
title: "wireless not working"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by guine on 2006-06-17
I am trying to get my linksys wmp54gs wireless card working, my computer is finding the card(it is detected during the boot and shows up when it do lspci in the terminal) but i have been unable to enable the card.  The card is listed in the under network settings but is disabled and clicking enable has done nothing.  At first it had nothing showing up for ip address and protocol so i manually changed the protocol to dchp(the same protocol that is working for my normal network card), when that didnt work I added the ip address that shows up with my network card for the wireless card but this has had no effect either.  Anyone have any ideas as to what i need to do to enable the wireless card?  Thanks.

---

### Post by stupidkid on 2006-06-18
You might have to try ndiswrapper. If you do, you'll have to remove your current wireless card modules (or blacklist them) and use the ndiswrapper module. This is how I got my prism card working.

---

