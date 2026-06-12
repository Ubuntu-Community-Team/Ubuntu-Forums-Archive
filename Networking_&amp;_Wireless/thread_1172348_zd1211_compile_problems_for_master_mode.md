---
title: "zd1211 compile problems for master mode"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by scales on 2009-05-28
Hi all.  I am trying to setup a ubuntu machine as an access point as described here:
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

I read that my particular usb wifi dongle needs different drivers (its a zydas zd1211)
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

So i went to the page they recommended, got the vendor based driver.  I installed the correct linux headers (2.6.28-11-generic as i just installed ubuntu via web so it is up to date) and build-essential.

When i try and make, i get the following error
"error implicit declaration of function 'eth_copy_and_sum' zd1205.c"
and it quits.

Can anyone help me out? offer an opinion on the matter?

UPDATE:
ok after asking in a few irc channels, i have been told that the makefile is not up to date to work with gcc4.4 and that it was meant for gcc3.3.  anyone know how i could update this?  i am not 100% sure this is the problem, but it is a place to start?

---

