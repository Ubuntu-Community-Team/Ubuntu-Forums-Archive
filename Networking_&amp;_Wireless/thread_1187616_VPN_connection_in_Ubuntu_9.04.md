---
title: "VPN connection in Ubuntu 9.04"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Oputres on 2009-06-14
Hi!

I had some problem setting up my VPN connection in Ubuntu 9.04 (using the flashback.name VPN service) and I finally got it up and running and thought I could share my experiences.

First of all I used this excellent tutorial: **[http://mateometzger.info/2009/02/19/vpn-in-ubuntu-904-jaunty/](http://mateometzger.info/2009/02/19/vpn-in-ubuntu-904-jaunty/)**

(note point 4)

But I didn't got it to work so I looked into my log file (var/log/syslog) after a failed connection and found the following:
```
nm-pptp-service-17371 fatal[get_ip_address:pptp.c:430]: gethostbyname 'pptp.flashback.name': HOST NOT FOUND
```

With the help of **[http://www.hcidata.info/host2ip.htm](http://www.hcidata.info/host2ip.htm)** I looked up what IP pptp.flashback.name were on and got the number which I put in the Gateway field under my VPN setting.

And it worked like a charm!

Hope this short tutorial will be useful for someone...

---

### Post by desmo on 2010-10-25
Hi,

Im running 10.04 and am using the same vpn service as you.
It works good for normal browsing but with Transmission it breaks the internet connection after about 5-10 minutes usage. I have tried with different settings in Transmission to not use so many peers etc. but with no sucess.
I also tried rtorrent (the terminal based client) but it did not help.
Any suggestions how to make it more stable, other settings or other client? 

best regards

---

