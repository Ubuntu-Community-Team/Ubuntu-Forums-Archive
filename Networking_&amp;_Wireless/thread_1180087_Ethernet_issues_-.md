---
title: "Ethernet issues -"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by dhavalbbhatt on 2009-06-06
Hi -

We had an electrical surge the other day, caused by lightning, which took out the power supply of my computer. I swapped that with a new one, and I can now power up my desktop, however, I can't get to the internet. My ethernet port (LAN port on the mobo) does not seem to be working. I am not sure, whether this is a problem with my mobo or a driver issue. Everything else seems to be working fine!

My hardware / OS -
ASUS M2N - SLI
Ubuntu 9.04 64bit


Would appreciate any help.

Thanks,
DB

---

### Post by puppywhacker on 2009-06-06
My experience with lightning is limited to this one time event. The motherboard was toasted via the network port, the capacitors were damaged and it smelled extra special =) black burn marks were clearly visible. And the ethernet lights didn't light up when connected, So I fear the thunder has fried your chips too.

---

### Post by Crafty Kisses on 2009-06-06
So let's see here, first we need to see the results of the following command:
```
lspci
```
Now make sure that your connection is enabled, so you can run these commands, and then try to connect to the Internet:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
Try that and see if that works.

---

### Post by jmbertolotti on 2009-06-06
Your network card is toasted, i had the same issue a few years ago and i didnt got that luck, my hdd was toasted too. 
):P

---

### Post by Crafty Kisses on 2009-06-06
> **jmbertolotti said:**
> Your network card is toasted, i had the same issue a few years ago and i didnt got that luck, my hdd was toasted too. 
):PNot necessarily, I think we should troubleshoot the issue first before we jump to any conclusions like that.

---

### Post by camper365 on 2009-06-06
Well, my sound card got fried a few days ago.
Along with my stereo's sound card, my dad's stereo's sound card, one of our tv's, my XM radio receiver, and my phone line (which is back now, but it fried all of our phones except the old corded one).
The lightning was within 100 feet of our house though.

---

### Post by camper365 on 2009-06-06
Well, my sound card got fried a few days ago.
Along with my stereo's sound card, my dad's stereo's sound card, one of our tv's, my XM radio receiver, and my phone line (which is back now, but it fried all of our phones except the old corded one).
The lightning was within 100 feet of our house though.

However, my laptop was fine. Probably because it wasn't plugged in.

---

### Post by puppywhacker on 2009-06-07
usually I'm a big fan of troubleshooting, but I'd substitute a probably toasted interface by a new cheap one.

---

### Post by Iowan on 2009-06-07
> **puppywhacker said:**
> usually I'm a big fan of troubleshooting, but I'd substitute a probably toasted interface by a new cheap one.To me, that IS troubleshooting.  If the problem goes away, it was *probably* the card (or something associated with it). If the problem remains...

---

