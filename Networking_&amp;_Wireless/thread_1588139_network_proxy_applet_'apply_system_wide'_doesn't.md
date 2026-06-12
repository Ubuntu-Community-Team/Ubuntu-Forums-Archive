---
title: "network proxy applet 'apply system wide' doesn't"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by cnkbrown on 2010-10-04
When I use the network proxy applet to set the proxy and the ignored hosts list, I use the "Apply System Wide..." button.

Opening a terminal, I can see the resultant proxy settings like this;

$ env | grep proxy
http_proxy=http://proxy:3128/
FTP_PROXY=ftp://proxy:3128/
ftp_proxy=ftp://proxy:3128/
all_proxy=socks://proxy:3128/
ALL_PROXY=socks://proxy:3128/
HTTPS_PROXY=https://proxy:3128/
https_proxy=https://proxy:3128/
no_proxy=localhost,127.0.0.0/8

If I follow this with;

$ sudo su bob
$ env | grep proxy
http_proxy=http://proxy:3128/
ftp_proxy=ftp://proxy:3128/
https_proxy=https://proxy:3128/

I see that the 'no_proxy' settings are not actually set system wide.

---

