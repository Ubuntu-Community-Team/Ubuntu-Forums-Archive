---
title: "gufw and IN/OUT"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by ygoe on 2011-01-09
Today I first tried out gufw to block some host that constantly tries to log into my FTP server which invalid user names. I managed to change the default rules to allow so that ufw wouldn't block my usual business. Then I added a rule to block all TCP from that IP to port 21. Working fine. :-)

But what is that IN/OUT distinction good for? I specify IP addresses as from and to, so why would I need to also say whether this is in- or outbound? An old Wiki article on ubuntuusers.de is dated Ubuntu 8.04 and doesn't make that difference at all.

---

### Post by marquinos on 2011-01-10
Hi! You have more info here: [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
IN is for incoming traffic (view from your computer).
OUT is for outgoing traffic
Best regards ;)

---

### Post by ygoe on 2011-01-10
That page doesn't explain anything more than the other I've read. It doesn't mention the in/out difference. And ufw doesn't even have such a feature. So what is it that gufw adds with this setting? Isn't gufw just a graphical frontend to ufw? So why can it do more then its base service supports? And still, whether traffic is inbound or outbound is determined by the IP addresses used. What will happen if I block incoming traffic from my IP to an external IP?

---

