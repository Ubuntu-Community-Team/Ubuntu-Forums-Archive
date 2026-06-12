---
title: "pppd problems"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by 5451vs5451 on 2006-07-07
According to the manual, the /etc/ppp/ip-up script and all scripts in /etc/ppp/ip-up.d/ should be executed when the link is available for sending and receiving IP packets. Similarly, the /etc/ppp/ip-down and those /etc/ppp/ip-down.d/ scripts should be executed when the link is no longer available. It worked exactly this way for breezy. Now I upgraded to dapper, and problems came. Those scripts other than ip-up cease to work. I used to configure the firewall by putting a fwbuilder-generated script in /etc/ppp/ip-up. Now I have to execute that script manually.

---

### Post by zxee on 2006-07-07
There are IMO big problems with ppp in dapper. Do a search on my name-I posted to a # of the related threads, filed a bug report (ignored for over a month then summarily rejected) and also created a poll. I don't see however that there has been any attempt by dev to rectify this situation.

---

