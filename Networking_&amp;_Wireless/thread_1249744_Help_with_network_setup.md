---
title: "Help with network setup"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Unspeakable Horror on 2009-08-25
Hello, I have a network setup as the png image shows, the problem I have is that I can't ping or connect with certain programs to the outside world from my Desktop or Laptop computers. If I ping from the server to the outside world it does work though.

The following seems to work fine since they are using the squid proxy installed in the server I guess.

Pidgin, skype, firefox, etc

Things that do not: (timeout)
Ping, traceroute, Anime O Matic,

Anime O Matic is a windows program that connects to port 9000 in a remote server to check what I have in my HD against a database (AniDB)


My home Server has the following installed:

Apache Webserver
BIND DNS Server
DHCP Server
SSH Server
Samba Windows File Sharing
Squid Proxy Server

And the rules in iptables are set to allow everything for testing purposes since I can't get it to work.

Desktop: Ubuntu 9.04/WindowsXP
Laptop: Ubuntu 9.04/WindowsXP
Server: Ubuntu Server 9.04

Does anyone know what could be wrong?

---

### Post by dmizer on 2009-08-25
You need to have NAT on the server.

However, I highly suggest that you reconfigure your network so that the router is in front of the server and just forward the necessary ports through the router. The DNS server is doing nothing under the current setup, and samba probably doesn't work right either.

Unless you have a well configured firewall on your server, this is actually a fairly dangerous configuration and your server is likely to be easily compromised.

You'll want something like this:
internet <=> router -> server, wireless, desktop

A router makes a better (and more easily configured) firewall anyway, unless you're using a distribution specifically meant to be a gateway.

Edit:
Alternatively (and less desirable), you can disable NAT on the router, and just use it as a hub.

---

### Post by Unspeakable Horror on 2009-08-25
> **dmizer said:**
> You need to have NAT on the server.

However, I highly suggest that you reconfigure your network so that the router is in front of the server and just forward the necessary ports through the router. The DNS server is doing nothing under the current setup, and samba probably doesn't work right either.

Unless you have a well configured firewall on your server, this is actually a fairly dangerous configuration and your server is likely to be easily compromised.

You'll want something like this:
internet <=> router -> server, wireless, desktop

A router makes a better (and more easily configured) firewall anyway, unless you're using a distribution specifically meant to be a gateway.

Edit:
Alternatively (and less desirable), you can disable NAT on the router, and just use it as a hub.

Yes, the setup you describe is what I previously had, unfortunately the router can't handle P2Pconnections and slowed down and crashed a lot, that's why I changed to the current setup since I can't buy a better router at the moment (forgot to mention, the server is in charge of P2P also). 

Thanks for your help! I'll see if I can secure the server and do the NAT thing then, since that's all I can do at the moment :(

Edit: you are right samba isn't working either.

---

### Post by dmizer on 2009-08-25
I've never had a single router that couldn't be configured to forward bittorrent ports, and what bittorrent software are you using on the server? Also, what is the make and model of your router?

You're better off temporarily disabling bittorrent (until you can figure out how to correctly configure it) in favor of a more secure setup.

---

### Post by Unspeakable Horror on 2009-08-25
> **dmizer said:**
> I've never had a single router that couldn't be configured to forward bittorrent ports, and what bittorrent software are you using on the server? Also, what is the make and model of your router?

You're better off temporarily disabling bittorrent (until you can figure out how to correctly configure it) in favor of a more secure setup.

Sorry, I wasn't clear, the router can be configured but it can't handle the load of http and amule (+ sometimes rtorrent) it slows down too much and becomes unresponsive.

The router is a Linksys wrt54g v8 changed to dd-wrt v24 firmware.

I followed this guide and successfully managed to add the NAT thing, it wasn't that hard lol.

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

Now all that remains is make sure this is actually secure and get samba back to working condition I guess, thanks for your help :)

---

### Post by dmizer on 2009-08-25
It wasn't that hard because you haven't actually configured it to filter any traffic. You still have zero security on the most vulnerable part of your network, and you'll still need to disable NAT on your dd-wrt router.

Do you have the same unresponsiveness with default firmware on the Linksys router? If not, then dd-wrt probably isn't an advantage for you. Doubly so if you're going to keep your current network configuration.

---

### Post by Unspeakable Horror on 2009-08-25
Yep I had the same problem with the original firmware, that's why I changed it but it didn't do much of a difference on it's performance even if I limited the connections to some low value it would still crash or slowdown sometimes.

I'm trying to find a guide on iptables so I can configure it correctly, do you have any suggestions?

I guess it would be much easier to put the router back before the server and everything else but I want to try doing it this way first.

---

### Post by dmizer on 2009-08-25
IPtables is far from "easy".

There are ways to configure it, but it's difficult to configure both NAT and have [SPI]("http://en.wikipedia.org/wiki/Stateful_firewall"). Here's a primer: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

You could try Firestarter which is a GUI interface for configuring IPtables, but Firstarter usually does more harm than good, as it doesn't interface well with Ubuntu. I am unsure if it's even in the Jaunty repositories.

GUFW is a gui frontend for a stateful firewall, but it can't handle NAT.

This is why I said it's better to have an actual router as your router, unless you're a pro with manual IPtables configuration.

---

### Post by Unspeakable Horror on 2009-08-25
Yeah, I know, I don't mind if it's not easy. I'll give it a try, I can always go back to the router anyway (or buy a better one in the future).

Thanks for your patience and help dmizer :):b:

---

### Post by dmizer on 2009-08-25
I would still strongly suggest favoring security over convenience, even if that means you have to disable some functions you regularly use.

I would suggest putting your router back in place and reducing your traffic load while you learn IPtables. There are other ways to do what you want to do, and it's possible you can try loading a [linux firewall]("http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions") onto your router, but I doubt that will fix your router's problem (it's probably toast).

Either way, be safe first and explore your options while operating under a secure connection.

---

