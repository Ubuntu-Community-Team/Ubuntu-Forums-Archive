---
title: "3g E220 help required"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by drdrake on 2009-03-07
I am using a Huawei E220 USB modem as my default(main and only) connection, and i want to network my Xbox (which is running XBMC) and various other things i do.

Problem im having is that its a USB modem and i need to possibly bridge the 
interface 'GSM (ttyUSB0)' to with my wired eth0.

I have read here and there but nothings been to helpful.

I don't wanna have to use my eeepc (windows xp) and use ICS to share the usb with the LAN into a router. 
(This PC contains all my shares and movies that i wanna watch on the xbox.(need the connection so i can download all the icons the images and content for my files))

Any and all help is great full..

---

### Post by netztier on 2009-03-07
> **drdrake said:**
> 

Problem im having is that its a USB modem and i need to possibly bridge the 
interface 'GSM (ttyUSB0)' to with my wired eth0.


Nah, not briding, but routing! Your idea about "internet connection sharing" was perfectly right - you can do that with your Ubuntu as well:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
or
[https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing)

You'll have to read a bit, so you can figure out how to adapt these guides to your network; for example, that 3G modem will make internet-facing interface probably "ppp0", an not "eth0" or eth0:0

[COLOR="Green"][INDENT]
Edit: this is waaaay easier now!

Just discovered it, but it works only with a 0.7x-Version of NetworkManager, so you'll need Ubuntu 8.10 or newer for this. Read this:

[http://www.fishpool.org/post/2009/01/15/How-to-share-a-wireless-connection-with-others-using-Ethernet-and-Fedora](http://www.fishpool.org/post/2009/01/15/How-to-share-a-wireless-connection-with-others-using-Ethernet-and-Fedora)

This guide is for *Fedora* Linux, allright, but nevermind. He describes so nicely how to define a new wired connection that I don't bother to copy that here. The only prerequisite on *Ubuntu* seems to be that you have to install the package **dnsmasq-base** via synaptic (or command line, if you prefer) before setting this up.

I just did all of this in less than 5 minutes and I am now sharing my 3G (incidentally also with a Huawei E220) to a Mac Powerbook via wired ethernet.
[/INDENT][/COLOR]

If you have the money to spare, there's devices like this on the market (or at least.. coming to the market), that will do all of the above in a single box:

[http://netgear.com/Products/RoutersandGateways/3GMobileBroadband/MBR624GU.aspx](http://netgear.com/Products/RoutersandGateways/3GMobileBroadband/MBR624GU.aspx)

Disclaimer: No, I don't work for netgear nor any of it's subsidiaries and I don't sell their products neither. I just thought "cool product!" when I saw it.


regards

Marc

---

