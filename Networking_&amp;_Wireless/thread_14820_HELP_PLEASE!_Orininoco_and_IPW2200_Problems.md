---
title: "HELP PLEASE! Orininoco and IPW2200 Problems"
date: 2005-02-10
forum: Networking &amp; Wireless
---

### Post by bond00 on 2005-02-10
I am having some problems with setting up wireless in Ubuntu.  I have an internal Intel 2200 and a Proxim 8470 Orinoco Gold.  I can't get either setup.  I know the installation finds and installs the 2200. I first have to go into networking and add the card, but it never asks me for the drivers or anything.  I just put in eth1, but the problem there is when I go to activate it, it will become unactivated a few seconds later.  I have tried installing the driver from scratch and that didn't work either.  

If I do a iwlist scanning, then it can find networks and I can even do iwconfig eth1 essid "name" and associate, but the I can't get a IP address.  I have tried dhclient and it still doesn't get an IP address.  That is my problem with that wireless card.

The other card I just bought because I wanted a nicer one to some stuff over the network and I thought Orinoco was a good brand and had lots of support, but the more I look, the more I'm beginning to change my mind.  I think it uses the Atheros chipset.  Is that right?  So does it use the madwifi drivers?  I have found conflicting views all over.  Also does it support monitor mode?  That is one of the main reason I got it.  I would really reall appreciate any help in either of these areas.  

When I install a new card do I install the drivers first and then go into Networking and activate or what's the exact order?  Through activating, if it doesn't even ask for the driver or type of card then how does it know which drivers to associate the card with and if they are installed?  I'm definetely no Linux guru, but I'm getting better.  I definetely need some help here though and any is appreciated.

---

### Post by wernst on 2005-02-12
Bondo,

I am by no means a Linux expert, but I must say that the Orinoco Gold card really is one of the best you can get. I have one myself, and it works auto-magically in Ubuntu.

I will say this though, my Orinoco WILL NOT get an IP address via DHCP from an access point where WEP is enabled, such as my house. This is true in Windows 98 and XP also, and across several machines. (This care has survived through THREE notebooks through the years.)

Once you enter in the correct Wireless info (wep key, SSID, and so forth) try entering IP info manually. (Odds are you could set your IP to 192.168.1.160, netmask sets to 255.255.255.0, and the router/gateway and DNS server to 192.168.1.1. Dollars to donuts this works.)

Let us know what happens.

Oh, and the Orinoco cards were among the FIRST to support monitor mode, which is why I intially got it. I haven't tried any of those tools under ubuntu yet though.

-Warr

---

