---
title: "Cisco VPN does not resolve names in Koala"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by wgandhi on 2009-10-31
Hi,

I compiled a version of cisco vpn using instructions from :
[http://ilapstech.blogspot.com/2009/09/cisco-vpn-client-on-karmic-koala.html](http://ilapstech.blogspot.com/2009/09/cisco-vpn-client-on-karmic-koala.html)

The compile went fine except for a warning:
"WARNING: could not find /vpnclient/.libdriver64.so.cmd for /vpnclient/libdriver64.so"

Started using /etc/init.d/vpn_client start
Connected to the WORK network. 
Now I cannot connect to any work servers. 

I used the same procedure on Jaunty and it worked fine.
I have checked the /etc/resolv.conf in both cases and it is the same.
This is a clean install of Karmic 64 bit.

-Wish

---

### Post by smitjel on 2009-11-01
Does this help?

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

---

