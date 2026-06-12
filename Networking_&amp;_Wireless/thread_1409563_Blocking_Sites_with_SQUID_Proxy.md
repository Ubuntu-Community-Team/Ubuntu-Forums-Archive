---
title: "Blocking Sites with SQUID Proxy"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by linuxrockers on 2010-02-17
I need to block some of my sites with SQUID Proxy. I added following lines to my SQUID configuration file but still the site remains unblocked.How to block it?

acl blocksites url_regex yahoo
http_access deny blocksites

I have also tried saving some url & filter content in a file and edited configuration as follows,

acl blocksites url_regex "/etc/squid/squid-block.acl"
http_access deny blocksites

The squid-block.acl file contents are,
.cricinfo.com
mp3

Please help me to block the sites !

---

### Post by Overcast32 on 2010-02-17
Depends - I'm not a squid guru, but if you want to go all out with Web Filtering, dansguardian works fanastic and it very configurable. 

This will work perfectly for Ubuntu 9.04: [http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic]("http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic")

As far as just 'squid' - I can't say.. but you could put a 127.0.0.1 in the hosts file maybe for that domain name? I'd guess if the proxy server can't find the domain, the clients couldn't either..

---

### Post by linuxrockers on 2010-02-27
Its working now..! Thank you so much!

---

