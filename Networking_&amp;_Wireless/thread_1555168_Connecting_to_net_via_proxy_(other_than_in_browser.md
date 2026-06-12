---
title: "Connecting to net via proxy (other than in browser)"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by bunburya on 2010-08-17
Hi guys, I have a problem regarding connecting to the net via my college's proxy.

Basically, my college requires us to connect to the net via a proxy configured by a PAC script. I have managed to connect to the internet for browsing purposes by entering the URL of the PAC script into the "Automatic proxy configuration URL" field in Firefox and/or System > Preferences > Network proxy. But I can't connect with any other application. I have tried connect with apt, Evolution and youtube-dl, nothing works. This is so even when I enter set the PAC config in the System > Preferences > Network Proxy, and have Evolution use the system defaults.

I've looked at the PAC script; it's a basic load balancer. IPs ending with odd numbers are sent to proxyA.xxx.com, IPs ending with even numbers are sent to proxyB.xxx.com, through port 8080. My IP ends with an odd number (right now) so I tried enter proxyA.xxx.com and 8080 into the manual proxy configuartion settings for Evolution but still no luck.

Anyone know what I'm doing wrong?

---

### Post by Naitsirhc Hsem on 2010-08-17
did you apply system wide in System > Preferences > Network proxy? if not, do so.

---

### Post by bunburya on 2010-08-17
Yes, sorry I should have said that I did.

I have also tried http_proxy="http://proxyA.xxx.com:8080" in command line.

---

