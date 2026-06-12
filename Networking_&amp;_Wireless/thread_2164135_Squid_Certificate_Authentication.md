---
title: "Squid Certificate Authentication"
date: 2013-07-30
forum: Networking &amp; Wireless
---

### Post by m3BhTne on 2013-07-30
Hey UbuntuForums users!

Struggling with a current issue. I am trying to install Squid3 to an Ubuntu server while using user-based certificates. When I try to connect is says that the proxy is refusing connections...

Here is config:
```
visible_hostname www.(businessSite).comhttp_port 80 accel defaultsite=www.lowrycomputer.com vhost
https_port 443 accel cert=/home/user/cert.cer key=/home/user/key.pem defaultsite=www.(businessSite).com vhost protocol=https
forwarded_for on


cache_peer (business IP) parent 443 0 no-query originserver ssl sslversion=3 sslflags=DONT_VERIFY_PEER front-end-https=on name=one
acl sites_one dstdomain www.(businessSite).com
cache_peer_access one allow sites_one
acl https proto https


cache_peer (business IP) parent 80 0 no-query originserver name=api
acl sites_api dstdomain www.(businessSite).com
cache_peer_access api allow sites_api
acl https proto https


acl computerIP src (business IP)


http_access allow computerIP



```

Any ideas?

---

