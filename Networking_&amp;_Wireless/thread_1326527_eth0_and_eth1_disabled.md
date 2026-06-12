---
title: "eth0 and eth1 disabled"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by nyp4life on 2009-11-14
hey everybody,

very strange problem i'm having. my ethernet ports are no longer working for some reason. i have had them up and running for a couple weeks now (since i installed 9.10) but all of a sudden they dont connect to the internet anymore. they were on statip ip addresses using the following /etc/network/interfaces config:

# This file describes the network interfaces available on your system
# and how to activate them.
#
# The loopback network interface
auto lo
iface lo inet loopback
#
# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.15.136
netmask 255.255.255.0
broadcast 192.168.15.254
gateway 192.168.15.1
#
auto eth0
iface eth0 inet static
address 192.168.15.135
netmask 255.255.255.0
broadcast 192.168.15.255
gateway 192.168.15.1

ifconfig shows them up and running but can't connect to the internet. luckily i also have wifi to get me through for now, but of course it's slower than ethernet. any ideas on how to get my ethernet working again?

thanks in advance

---

### Post by t0mppa on 2009-11-14
Ok, one question about your network topology: why do you have two ethernet ports connected to the same subnet? Seems a little redundant.

As for troubleshooting, can you ping the gateway? What about outside addresses by their domain name and/or IP address (ie. ping [www.google.com](www.google.com) vs. ping 74.125.79.99)?

---

### Post by nyp4life on 2009-11-14
hey t0mppa,
first thanks for the quick reply!
now about my network, i set it up this way only by guess & check. my first try was having the same values for everything except the ip address. so i then changed the broadcast for one eth port and it worked. i had no idea on how to set up static ip's in linux (just recently dropped windows lol). so once i found an 'interfaces' file that worked, i stopped. if this was not a correct 'interfaces' file, i am open to suggestions. sorry, noob here :-|
ok so i can successfully ping my router, but pinging google returns 0% successful packets.

---

### Post by t0mppa on 2009-11-14
> **nyp4life said:**
> hey t0mppa,
first thanks for the quick reply!
now about my network, i set it up this way only by guess & check. my first try was having the same values for everything except the ip address. so i then changed the broadcast for one eth port and it worked. i had no idea on how to set up static ip's in linux (just recently dropped windows lol). so once i found an 'interfaces' file that worked, i stopped. if this was not a correct 'interfaces' file, i am open to suggestions. sorry, noob here :-|

It is correct and all, what has me confused is why you're using two cards to get connected to one network, when one card would be enough for that?

> **nyp4life said:**
> ok so i can successfully ping my router, but pinging google returns 0% successful packets.

You tried pinging Google by the IP too? In that case are you sure your router is still connected to Internet? Have any other computers that can connect through it just fine?

---

### Post by nyp4life on 2009-11-14
the router is connected to internet. two other computers and this one (when wireless is enabled) all connect. 
about my two cards, i use one for local network and one for internet. one is good enough but my motherboard comes with two and i dont like to waste things lol.

---

### Post by t0mppa on 2009-11-14
Ok, to just make life simpler, why don't plug out one of the Ethernet cables and just try with one card for starters (same steps as before). Once you get that working, you can go back to using both, if you really want to.

If that didn't help, let's check your routing table, in hopes that it'd be a problem with that one. Open up a terminal, run **ip route list** (when the wireless isn't connected and the wired is) and post back with the results.

---

### Post by nyp4life on 2009-11-14
ok uplugged one ethernet cable and all is working. although for some reason i still can't ping google (domain name or ip) using 'network tools'... oh well, at least the internet is working. i'll just stick to one active ethernet port. the other one looks so empty now lol. thanks t0mppa!

---

