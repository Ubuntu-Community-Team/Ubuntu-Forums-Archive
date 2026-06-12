---
title: "OpenConnect stopped working all of a sudden since Thursday"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by deepaknet on 2011-03-05
Dear Ubuntu Team,

I am unable to connect to my Work Cisco VPN as it fails with the following error message:


Error fetching HTTPS response
SSL negotiation with <IP Address>
Connected to HTTPS on <IP Address>
Error fetching HTTPS response
Creating SSL connection failed

I haven't been getting this all these days. I checked with Helpdesk and they have confirmed no software updates or configuration change has gone into the VPN server as well. The commandline I am using to connect is below:

sudo openconnect  <IP Address> --script /etc/vpnc/vpnc-script

Can you help with what is going wrong? Also is there a way I can configure my openconnect to ignore sSL errors. I tried hitting the following URL in Chrome:

https:// <IP Address>

and it gave an error like 

The site's security certificate is not trusted!
You attempted to reach <IP Address>, but the server presented a certificate issued by an entity that is not trusted by your computer's operating system. This may mean that the server has generated its own security credentials, which Google Chrome cannot rely on for identity information, or an attacker may be trying to intercept your communications. You should not proceed, especially if you have never seen this warning before for this site.

Is there a way I import it to Ubuntu's Trusted Certificate store (how do we do that) so that OpenConnect can connect hassle-free to the server?

---

### Post by dwmw2 on 2011-03-09
[http://twitter.com/#!/dwmw2/status/25912957502234624](http://twitter.com/#!/dwmw2/status/25912957502234624)

Please report your issue to the openconnect-devel mailing list, and we should be able to solve it.

---

