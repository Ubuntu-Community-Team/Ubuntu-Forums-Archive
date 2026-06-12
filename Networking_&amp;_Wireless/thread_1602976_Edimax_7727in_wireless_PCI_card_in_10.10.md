---
title: "Edimax 7727in wireless PCI card in 10.10"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Nickster74 on 2010-10-22
Hi Guys,
 
I'm looking for some help,
 
I have Maverick Meerkat running perfectly on my laptop and have loaded as dual boot onto my old XP pc as well, I'm quite a newbie and working my way through Ubuntu for Non Geeks.
 
Problem - apparently this PCI card - Edimax wireless N PCI 7727in card is supposed to work out of the box, it came with the Ralink drivers for Ubuntu RT2860.
 
the network manager finds the homehub and tries to connect but just continually tries and never actually does it, the card works fine with XP so i know it's not faulty.
 
if it was a driver fault would the card be working at all? would it try to find the network manager? 
 
I bought this card as previously i was using a Dlink DWA-140 and gave up trying to make it work, this card is advertised as Linux compatible in the Ubuntu forums list and on the card.
 
would love a steer in the right direction.
 
cheers Nickster

---

### Post by Nickster74 on 2010-10-22
Hi Me again,
 
if i can't get the edimax card working has anyone had any luck in making the Dlink DWA-140 usb wireless N card work with 10.10 Meerkat?
 
at the end of my tether...............................

---

### Post by flash63 on 2010-10-22
Hello,
for your DWA-140 you must block rt2800usb
> echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
Restart.

More Information about the Edimax wireless N PCI 7727in
```
lspci -nnk | grep -i net -A2
lsmod
sudo iwlist scan
```
Mark your own Network

---

### Post by Nickster74 on 2010-11-08
HI Everyone,
 
Resolved this by uninstalling Ubuntu and replacing with Zorin o/s 3 which is by far a superb system.

---

