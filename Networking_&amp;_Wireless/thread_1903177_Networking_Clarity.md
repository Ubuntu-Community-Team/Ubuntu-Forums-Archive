---
title: "Networking Clarity"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by NickellossAych on 2012-01-01
Somehow I've gotten what I want to work, but I don't know how/why.  I would like clarity on the following.

I desired to set up a static IP address on my Ubuntu server so that I could remote in from my computer upstairs.  The server is running Ubuntu 10.04 LTS.  I read that in order to set up a static IP, you must edit /etc/network/interfaces. What I don't understand then, is the point of System > Preferences > Network Connections.  I set a static IP in there and it did not change the /etc/network/interfaces file.  Now ifconfig shows the computer having my desired static IP address, but the System > Preferences > Network Connections connection is set to Automatic DHCP.  

Furthermore confusing me is how editing the IP address on the computer fits in with setting a static IP address on my router.  I'm using an Linksys WRT150N with DD-WRT v24.  I reserve the IP to the appropriate MAC address.  Is it necessary to set the static IP in both locations or only one or what?

Now if that wasn't enough, my Xubuntu computer is working differently.  It's /etc/network/interfaces file is set to ```
auto lo
iface lo inet loopback
``` and the Settings > Network Connections is where the static IP is set, and it all seems to be working completely.

So between the two computers, both have successful static IP's, but were set in completely opposite ways.  Can anyone clarify why some things do/don't work?

---

### Post by LewisTM on 2012-01-02
It's much simpler to have your router set the static IP. It hosts a DHCP server which will assign IPs to all connected boxes. On Static, the Linksys will always assign the same, specified IP address to the device with the MAC address. On Dynamic, the address will be the next available and can vary.

Set your computers to automatic IP and have the router manage the rest. One case where you would want to set an interface-side static IP would be to gain a few microseconds on your initial network connection.

---

### Post by NickellossAych on 2012-01-03
Thanks. That's what I've set it up recently. All my home's computers are DHCP with the router reserving IP's to the MAC's. I was more curious about why changing "Network Connections" didn't change the /etc/network/interfaces file.

---

### Post by redmk2 on 2012-01-03
> **NickellossAych said:**
> Thanks. That's what I've set it up recently. All my home's computers are DHCP with the router reserving IP's to the MAC's. I was more curious about why changing "Network Connections" didn't change the /etc/network/interfaces file.

The term "static IP address" is not exactly what you (and many others) think it means.  The term *static* referrers to how the interface is configured.  The can be either statically (via a text file i.e /etc/network/interfaces) or dynamically via a dhcp server.

In fact the term static IP address has nothing directly to do with an address that is immutable (unchanging).

To further complicate the situation there now are GUI based apps that will configure an interface (manage it) either statically or dynamically.

You router (via reserved IP addresses) is always a dynamically assigned IP address as it uses a dhcp server to assign the IP address.

So we have ```
static IP address = file based interface management (IP address) 
dynamic IP address = DHCP server managed interface management

immutable IP address = unchanging IP address
```

---

