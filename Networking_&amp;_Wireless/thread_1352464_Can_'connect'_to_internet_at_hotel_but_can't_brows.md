---
title: "Can 'connect' to internet at hotel but can't browse internet"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by GammaPoint on 2009-12-11
Hi everyone, I'm attending a conference over the next couple of days at a local hotel. Problem is I can't connect to the wireless internet with my Ubuntu 9.10 T61 laptop. I connect to the internet just fine wirelessly from home. 

Technically I 'connect' to the network and can ping websites but I can't SSH to remote machines, nor can I browse the web. 

I'm going back there in a couple hours and was curious, which commands should I get the output of so that I (with your gracious help :) ) can debug this later tonight when I come home?

From what I've read on these forums the output of 
```
sudo lshw -C network
```
might be useful. Any others?

Best,
GP

---

### Post by GammaPoint on 2009-12-11
Sorry for the mistake. I had 10.04 instead of 9.10 in my above post and was moved to this forum by mistake. Could someone please move me back to the wireless forum (and edit my title :) )?

---

### Post by Iowan on 2009-12-11
Check */etc/resolv.conf* to see if you are getting nameservers.

---

### Post by Filipek on 2009-12-13
Are you sure you are on the "open" network? What sites are you actually able to ping?

According to my experience with hotel networks, those are open, you can connect to them but afterwards, you have to open the web browser which leads to to their internal website....

As soon as you register there (pay maybe...) the cookie is stored on your machine and you are given the access let's say for limited amount of time...

Just quessing but are you sure this is not the case?

---

### Post by kidknapp on 2010-07-22
What I've encountered is this same problem but Firefox won't redirect to the internal website...Usually this internal site requires a login or consent to terms, but if you can't access this page the Wi-Fi doesn't connect properly. I've heard of taking the DHCP and DNS settings from a dual boot of Windoze and applying them into the network wireless settings fields, making a new custom connection - this is cumbersome.... What works for me- On 7, Vista,Or Xp, DB Heron or above - is connecting to the hotel wifi in Windoze and then rebooting into Ubuntu - the router will usually continue to allow your machine based on its MAC address - once your time limit suspends do it again...Still cumbersome...Maybe someone will leave a better suggestion beyond this, but for now we are victims of suspicious browser redirecting "free" wi-fi tracking management software...I digress...

---

