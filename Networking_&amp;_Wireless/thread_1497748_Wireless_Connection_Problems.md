---
title: "Wireless Connection Problems"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by hitmen on 2010-05-31
I am actually using backtrack but I got no ubuntu experience. 

In short, this is the message after running dhclient.
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping

What I have done:
cat /etc/network/interfaces     // to get interface
auto lo
iface lo inet loopback 

auto eth0
iface eth0 inet dhcp 

auto ath0
iface ath0 inet dhcp 

auto wlan0
iface wlan0 inet dhcp 

I used wicd manager and it tells me "This network requires encryption to be enable.d"

Questions:
How am I supposed to get my Internet connection up?

How am I supposed to set up encryption?

Where am I supposed to enter the password for my access point? 
(I am using a MiO box. Singaporeans will know what I mean)

What is the difference between ath0 and wlan0? Are they both wireless?

How am I supposed to know what the nameserver is supposed to be?

---

