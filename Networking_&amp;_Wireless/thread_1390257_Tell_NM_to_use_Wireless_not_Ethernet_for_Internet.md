---
title: "Tell NM to use Wireless not Ethernet for Internet"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by Who on 2010-01-25
Hi all,

I am getting my internet connection from a wireless router. I have a computer connected via ethernet, which I want to share the wireless connection to.

I've used NetworkManager to set up static IPs for the two boxes on the ethernet network and they are 192.168.2.1 (desktop) and 192.168.2.2 (laptop)

Internet <-Wifi-> desktop <-ethernet-> Laptop

The laptop has gateway set to 192.168.2.1. The desktop has the gateway in the ethernet configuration set to nothing, but I've also tried 192.168.2.1

Now. When I have ONLY the wireless connected, the desktop can see the internet. Whenever I plug in the ethernet cable and the connection between the laptop and the desktop is made, I can _no longer_ get internet on the desktop, let alone share the internet to the laptop.

So, before I mess about with sharing things, how do I tell NM or whatever that the connection to the _internet_ is over , always

Thanks in advance,

Who

---

