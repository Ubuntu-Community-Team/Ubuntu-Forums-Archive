---
title: "Transparent proxy! (Squid3)"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by salvor_hardin on 2009-06-12
Hello!

I want to set up a transparent proxy using Squid3. I already installed and started, configured Squid to work as cache proxy and that is transparent. What I don't know is how to set up IP tables or routes. 

1. Linux Ubuntu 64 is Squid Proxy: 192.168.2.88
2. Airlive Gateway MW 2000S is gateway for network 192.168.2.254 (NAT mode)

Gateway is powerfull and has lots of options, including routes option and IP tables option. ( Will post a screenshot if neccessary) 

Im giving internet access through wireless hotspot system, and all potential clients IP-s are 192.168.1.0/100, I want to force them to use proxy web cache because I cannot enter proxy settings manually for each one of them. 

I need some help, i found lots of stuff but I dont understand quite good... Can someone explain this to me? any help is great!!!

I guess I need to direct all traffic from my NAT gateway  to port 3128 to my machine...but I already did set up for external proxy on gateway...All I found on internet is setting it up whrn having proxy and router on the same machine.

---

### Post by salvor_hardin on 2009-06-12
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=117326&stc=1&d=1244800162[/IMG]

---

### Post by jaimerosario on 2011-03-26
Try the following:

Destination
IP Address: 192.168.1.0
Port: 80

Translated to Destination
IP Address: 192.168.2.88
Port: 3128
Type: TCP

---

