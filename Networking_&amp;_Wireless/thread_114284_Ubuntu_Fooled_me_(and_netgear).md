---
title: "Ubuntu Fooled me (and netgear)"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by slime_not on 2006-01-08
I tried Breezy Badger 5.1 live CD and it picked up my netgear wireless wg311 with no problem. I then installed BB5.1 and it cannot find my router.It does see the card in the device panel.

I used the default install. Should I reinstall with a different setup to more closely mimic the software detection in the live CD? 

My system is a desktop at the other end of my house, so I cannot connect to the net to dl anything else.

---

### Post by gnu2tux on 2006-01-08
Hi,

 Are you talking about a problem with a wired connection to your router, or are you talking about a wireless card?

If you want to check that a card exists, type ifconfig at the terminal and check for eth0 or wifi0.

If you have a cable, you use eth0 for the network card.
If you have a wireless card, you usually use eth1/wifi0 for the wifi card.

Make sure that your router has DHCP installed so that it provides your Linux box with an IP, DNS and internet routing information.

After you've done that, visit the network configuration tool and ensure that a valid IP address is given to your pc and you can ping an IP on the net, for example google:

$ping 64.233.187.99

If you can ping that, then try using the name:

$ping google.com

If that doesn't work, it's a problem with your DNS information, check DHCP on the router, or check DHCP (auto configuration) is enabled on your network tool.

Regards,

Al.

---

