---
title: "WEP/WPA - wrong detection"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by decibyte on 2010-05-16
I've got a strange problem.

When trying to connect to my wireless network, the Wireless Network Authentication comes up, asking me for the password. That's fine, but the security method dropdown doesn't list WPA - only WEP and LEAP. But I'm using WPA on my network.

Initially, I thought it was because of an outdated driver (using ndiswrapper and a Windows driver). But when I try connecting to some of the other networks available, the drowdown contains WPA as it should.

I tried forcing it to use WPA via the Network Manager saved connections, but when I connect, it doesn't use the saved connection but creates a new one, prompting for a WEP password.

How come it is mis-detecting the protection method for my network? Is there a way to force it to use WPA?

I'm running Lucid. The card is a Texas Instruments ACX 111 54Mbps Wireless Interface (according to lspci).

---

