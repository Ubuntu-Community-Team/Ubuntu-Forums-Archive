---
title: "Wireless network - 1 SSID, 2 access points - Can I specify which I connect to?"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by adamr on 2013-01-15
I have one wireless network at home, with a router and a wireless network extender, running in network extender mode.

Devices at home see it transparently, as one network, and in theory should just connect to the one offering the strongest connection. The problem is, where I use this laptop (64bit Quantal) sits right in-between the two access points, so it frequently drops from one to try to connect to the other.

My question is, given one network with multiple access points (wifi scanners can see both), is it possible to specify which I connect to? Either that or change (remove?) the time before it re-scans and finds the strongest signal again?

---

### Post by haqking on 2013-01-15
> **adamr said:**
> I have one wireless network at home, with a router and a wireless network extender, running in network extender mode.

Devices at home see it transparently, as one network, and in theory should just connect to the one offering the strongest connection. The problem is, where I use this laptop (64bit Quantal) sits right in-between the two access points, so it frequently drops from one to try to connect to the other.

My question is, given one network with multiple access points (wifi scanners can see both), is it possible to specify which I connect to? Either that or change (remove?) the time before it re-scans and finds the strongest signal again?

you can specify the Access Point MAC address in your network settings.

It is known as the BSSID (Basic Service Set Identifier)

So look for the BSSID field in whatever network manager application you use which will depend on your Desktop environment etc, then put in the MAC address of the AP you want to use

and then it probably wont work at all ;-)

---

### Post by adamr on 2013-01-15
> **haqking said:**
> you can specify the Access Point MAC address in your network settings.

It is known as the BSSID (Basic Service Set Identifier)

So look for the BSSID field in whatever network manager application you use which will depend on your Desktop environment etc, then put in the MAC address of the AP you want to use

and then it probably wont work at all ;-)

Well, I managed to discover arping to get the mac of my router, and I've set that as my BSSID, so we'll see what happens.

Thanks for the fast reply!

---

### Post by adamr on 2013-01-16
Any ideas how to make this persistent?

I started having it drop out again, went and had a look at BSSID and it had reverted back to blank :/

---

