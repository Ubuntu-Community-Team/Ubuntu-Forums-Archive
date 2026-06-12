---
title: "Can't detect specific wireless network"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by SpacyRicochet on 2009-07-05
I'm currently working from an Asus A6Ja laptop on Windows. They have a wireless network here, which is detected normally on Windows and OSX from Apple. This means that it can be selected from the 'List of wireless networks' on both respective systems.

However, Ubuntu 8.10 (fresh install from a live-CD) somehow doesn't detect the network normally. It doesn't appear in list of wireless networks (while the other networks in the neighbourhood do appear) and when I try to connect to it through 'Connect to a hidden wireless network', it takes a long time attempting a connection and eventually gives up and asks me for the credentials again. As far as I can tell, it doesn't actually make a connection (as in, the animated icon of the swoosh with the grey and green ball doesn't change into one with two green balls).

Can anyone think of a reason why the network is detectable in Windows and OSX and not in Ubuntu? The network is configured with WPA2-Personal (or WPA2-PSK, depending on what you check that with) and uses a rather large MD5-style as a password to connect.

One suspicion I have is that the MD5 password is based of a normal keyphrase and after entering it in Windows and OSX, it is passed 'as is' and authenticated, while Ubuntu perhaps throws another MD5-hash over it. But this sounds like crap. Why would an encryption work that differently through systems?

---

