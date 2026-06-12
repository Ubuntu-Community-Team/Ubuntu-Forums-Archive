---
title: "Firefox 3.5 and Pidgin does not work on 3G Connection"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by chamtem@gmail.com on 2009-12-29
Hi Guys,

Im using Ubuntu 9.10 and I use Vodafone E220 3G modem for my internet connection (PPP). Establishing the connection works like charm. 

But most of the time after establishing the connection Firefox and Pidgin are unable to find the connection. (firefox NOT in offline mode), I have to disconnect and reconnect many times to get things done. But Skype works nicely with this connection

Any workaround for this problem?

Thanks

---

### Post by chamtem@gmail.com on 2009-12-29
Hi Guys,

I found a clue, Issue is connection establishment does not set the primary DNS and secondary DSN ips. If I use ip address instead of domain name, Firefox can find the site. I guess skype also connects using ip address instead of domain. 

I want to know is there a way to set primary and secondary DNS manually for PPP connections?

Thanks

---

