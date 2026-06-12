---
title: "Need help setting up wireless internet, without wired internet"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by LA1Z24 on 2008-12-11
Hello everyone.  I'm having some issues here with my laptop.  It's an HP DV6770se with an Atheros 5007 wireless chipset.  I've had it running in the past but had to reinstall Ubuntu 8.10 because of a newb mistake.  Since then, I've switched from using FIOS internet, to using my cell phone as a modem...Actually using my cell phone as an ad hoc access point.  It works great in windows, but would like to set it up in Ubuntu.  Problem is my wireless card is lacking the wireless aspect...And I have no ethernet internet to install drivers.  So how would I go about downloading what I need in Windows and installing it manually in Ubuntu?  Thanks

Jay

---

### Post by Niels Olson on 2008-12-11
bump.

See, interestingly, I'm trying to do much the same thing but my wireless card is a Broadcom 43xx (4311, specifically), which is famously ill supported in Linux (look up ndiswrapper and b43 drivers). I have tried the b43 driver and the ndiswrapper driver. However, the b43 developers recently declared ad hoc networking now works under the b43 driver. I also chatted with an OpenSuSE forums administrator who said he's got ad hoc networking under the b43 driver in SuSE. I corresponded with a developer on the bcm43xx-dev mailing list (off list) and he verified ad hoc networking works, at least on his card (a 4306, and his brother's card, a 4318 ). 

In frustration, I tried to set up Ubuntu's ad hoc networking on another ubuntu laptop, this one with an Intel 2200 card. Didn't work. Interestingly, I set up an ad hoc network on my Macintosh under OS X and my Ubuntu/Intel2200 was able to *join* the ad hoc network. ifconfig reported eth0, eth1, eth1:avahi, and lo. Avahi is the major Linux implementation of the zeroconf protocol (which is the protocol you use for "ad hoc" networking)

So now we have atheros, intel, and broadcom cards, and it seems that the common factor is *Ubuntu* can't *start* an ad hoc network. We even have counterpoint from SuSE that it works for them.

hmmmmmm.

Any thoughts?

---

### Post by Niels Olson on 2008-12-11
seems I jumped on the wrong issue. I was on 8.04. I just upgraded to 8.10 and found myself with a situation that even more closely approximates yours. I think you want this: 

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404)

---

### Post by Niels Olson on 2008-12-12
Seems that if you want your Ubuntu to *start* the ad hoc network, you will also need the dnsmasq package

---

