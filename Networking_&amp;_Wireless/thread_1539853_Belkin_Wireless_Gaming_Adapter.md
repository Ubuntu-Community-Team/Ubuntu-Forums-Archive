---
title: "Belkin Wireless Gaming Adapter"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by Masamune12003 on 2010-07-27
Okay, I've searched everything I can think of to find out if this or something similar has already been solved but I didn't find anything, that's not to say it hasn't already been done because I don't understand enough of what I'm using to search properly, if it has then I apologise.

The problem I have is connecting to the internet using Ubuntu 10.4 and my Belkin Wireless G Gaming Adapter, I'll try and give an overview of my setup.

PC - BelkinWirelessAdapter - Router.

The PC is connected to Adapter via ethernet, I set up the Adapter through my web browser to connect to my router, it finds the router perfectly but no matter how I set up the IP settings etc... it won't come up saying it is connected to the internet, the connection to the adapter itself seems okay as long as I am only trying to get into the adapter itself which requires a particular IP address, this address can't be used to get online though, so when I change it to what works on every other system I've used nothing happends, nothing happens when I use DHCP either.

I'm a complete Linux noob so please make any responses as simple as possible lol.


If you need more information I will try and provide it.

Cheers!

---

### Post by aeiah on 2010-07-27
ive used a similar setup before. your wireless gaming adaptor is basically the same as a wireless router in client bridge mode by the sounds of things. perhaps you should search with this in mind.

my modem/router is 192.168.0.1 and assigns IPs via DHCP to clients in the 192.168.0.60-69 range

my bridge has a static IP of 192.168.0.2

because my modem/router is the one handing out IP addresses, when i connect to my bridge (which is connected to the modem/router wirelessly) i get given an ip of 192.168.0.60


i dont know what your belkin control panel looks like but you should probably set its IP similar to how i have (ie, set it to the same subnet as your modem/router ... if your router is 192.168.1.154 give it the number 192.168.1.2 for example), and make sure DHCP is off on the bridge, and on on your router.

if that works, you could think about setting up a purely static ip i suppose.

on your linux machine, you may want to use network manager to refresh things, or you may find this more helpful
```

sudo dhclient

```

---

