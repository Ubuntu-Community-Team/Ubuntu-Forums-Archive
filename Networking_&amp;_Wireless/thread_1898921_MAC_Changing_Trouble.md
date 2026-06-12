---
title: "MAC Changing Trouble"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by Polypro on 2011-12-22
Ubuntu 11.10 on an Acer TimelineX 11.6" I swapped out the OEM Broadcom card with an Intel 633 Centrino-N 450mbs card. The swap went well, even adding the third antenna, and I have the card working fine. I connect to a Buffalo 450mbs router.

My problem is with changing the MAC. This is about privacy and not anything malicious. I'd just like to decrease my footprint when connecting to AP's that aren't my own, that's all.

Using the Terminal  I can do:

ifconfig wlan0 down
ifconfig wlan0 hw ether ad:dr:es:sh:er:ex
ifconfig wlan0 up

...and receive no errors. If I then ifconfig, it shows the new address, so far, so good. I'm very familiar with when it doesn't work, having tried the Broadcom card and getting SOIFFIOC (sp?) errors about too many files open

I can also use macchanger -r or the macchanger-gtk GUI and also change the address with no errors.

The problem comes when I try to re-acquire my Buffalo AP. It will sit there scanning for a long while, eventually pop up the password screen (which I assume means it see's the new MAC) but then never connect. It just keeps popping up the password box again, and again. 

Should this just 'work', or do I need to do something in the Network Manager GUI where it lists the wireless networks? Right now there is just my original AP, Auto Connect, DHCP Automatic, and it lists the wlan0 card and the burned in MAC. I've also tried 'Cloning' from here, but again, no connection. 

Thanks in advance,

P

Edit: P.S. There is no MAC filtering on the router, and I've even tried clearing out the DHCP reservation for the old MAC/IP.

---

