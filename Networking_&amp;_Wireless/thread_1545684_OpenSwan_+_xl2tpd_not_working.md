---
title: "OpenSwan + xl2tpd not working"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by ghostryder on 2010-08-04
Hi,

I'm currently setting up a VPN Server using Ubuntu plus OpenSwan and xl2tpd. I used this tutorial for the installation and configuration process:

[http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html](http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html)

I got that message in the log files of ipsec:

STATE_QUICK_R2: IPsec SA established transport mode 

So it seems that is working.

I'm now stuck were xl2tpd should take over... I've opened port 1701 and started xl2tpd using "xl2tpd -D" to see all debugging messages, but the daemon just tells me that it's listing on 0.0.0.0 Port 1701. But there is anything coming in... I'm using a Windows client on the other side for testing VPN. Configuration again is based on the above posted link. 

Does anyone have an idea why xl2tpd is not getting anything? 'netstat -antu' also shows it's listing on port 1701...

This is the configuration of xl2tpd:

```
[global]
ipsec saref = yes
listen-addr = 192.168.0.22

[lns default]
ip range = 192.168.0.100-192.168.0.105
local ip = 192.168.0.99
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile= /etc/ppp/options.xl2tpd
length bit = yes

```

Thanks for all your help!
Regards, g.

---

