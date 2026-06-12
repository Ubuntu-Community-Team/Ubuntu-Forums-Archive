---
title: "Wifi DHCP Problem"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by atomicmoose on 2006-02-19
I just loaded Ubuntu 5.10 in my IBM Thinkpad R51. Everything is working great, except the wifi connection.

I installed GTKwifi and it seems to be working as intended, however I cannot get an IP address from my router. I have tried changing the SSID, WEP Key, I removed my access list. Nothing seems to work. I can authenticate to the network, it gives me a signal strength, and even says that I am connected, however the logs show that DHCP is failing. I am not being assigned an IP. I don't feel that this is a problem with the router since my other 2 laptop can connect fine and DHCP assigns them an IP.

Am I missing something here? Any assistance you can offer is appreciated.:)

---

### Post by suRoot on 2006-02-21
I had exactly the same problem with my Thinkpad T40p... you can lookup some of the earlier posts I made about it by looking at my user account.  After a few weeks I finally threw my hands up and found an old D-Link PCMCIA card which works fine out of the box.  I'd guess our laptops use similar, if not the same, cards.  It just seems to be a problem with the drivers for that card.  If you ever find a solution, I'd like to hear about it.  Absoultely nothing I did ever got the card working.

---

### Post by atomicmoose on 2006-02-22
[QUOTE=suRoot]I had exactly the same problem with my Thinkpad T40p... you can lookup some of the earlier posts I made about it by looking at my user account.  After a few weeks I finally threw my hands up and found an old D-Link PCMCIA card which works fine out of the box.  I'd guess our laptops use similar, if not the same, cards.  It just seems to be a problem with the drivers for that card.  If you ever find a solution, I'd like to hear about it.  Absoultely nothing I did ever got the card working.[/QUOTE]It actually has been working sporadically of late. I changed my encryption key from ACSII to HEX and it has been better.

It is a strange problem. If I find anything more concrete, I will be sure to post.

---

