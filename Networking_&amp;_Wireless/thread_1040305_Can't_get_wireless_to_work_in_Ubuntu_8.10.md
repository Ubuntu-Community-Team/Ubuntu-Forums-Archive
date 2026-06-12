---
title: "Can't get wireless to work in Ubuntu 8.10"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Krydox on 2009-01-15
Hi, I just installed Ubuntu 8.10, everything seems to work fine, I had to do the installing process with a wired connection because I just can't seem to get wireless to work and I know it can cause some trouble if you don't have internet during installation.

It worked fine with older versions but somehow this seems so much harder and I'm dealing with terms I don't even know like SSID / BSSID so I don't know what to do to get it working..

Any help would be appreciated.

---

### Post by movingover on 2009-01-15
An SSID is essentially a number that positives identifies a wireless network, which you probably don't need unless you don't broadcast your network using router security settings.

Have you tried turning off that sort of thing (not broadcasting, turning off WPA/WEP encryption, etc) to get it working first? If you still can't get your wireless to work with zero security, then you have a problem with Ubuntu. Otherwise it may be a problem with figuring out the correct configuration of your network.

Note: if you turn off your wireless security, remember to turn it back ON when you're done troubleshooting! :)

Hope this helps!

---

### Post by Krydox on 2009-01-15
Thanks for ur fast reply, well the only security I have on my router is a MAC filter, and the MAC of the device in my laptop is already in the list..

And I just tried turning off SSID broadcasting but it didn't do anything, and what I don't understand is that I >have< to fill in something in the SSID field.

---

### Post by DFord425 on 2009-01-15
The SSID is the name your router brodcasts. If its a linksys router, the default SSID is usually Linksys. Thats what your have to put in the SSID field.

---

### Post by Krydox on 2009-01-15
Well I got it to work, the problem was actually my network card. It's an Atheros 802.11 known as AR242x, and I found a guide on how to make that one work.

I'll link it here incase anyone reading this has the same problem: [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/")

Thanks for your help though, and to DFord425: yea i figured that too meanwhile, feel kinda stupid for not seeing it earlier lol.

---

