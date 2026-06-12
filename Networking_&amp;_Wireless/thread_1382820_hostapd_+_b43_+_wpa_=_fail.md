---
title: "hostapd + b43 + wpa = fail"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by imrazor on 2010-01-16
Got a strange problem I'm trying to iron out. To summarize, I've got a Dell Dimension 4550 with a Buffalo 54G card (identified by lspci as a Broadcom BCM4318) running Ubuntu 9.10 desktop (not server). My goal is to set it up as an access point/firewall/router/PPPoE client. After a couple of days I've made some progress, but I've hit a stumbling block. As an open access point, it works pretty well. Everything but my iMac (running OS 10.6.1) can connect to it and surf the internet (it's double NAT'd through my existing router, which will eventually be replaced.) The imac's log shows Disassociated due to inactivity after being connected for ~5 secs. When I try to activate WPA, things get much worse. No OS X client will connect (10.5, 10.6 or iPhone) nor Ubuntu 9.04. Oddly, an XP client will connect, running on the same hardware as the Ubuntu client. Does anyone have any pointers for troubleshooting WPA problems with hostapd? Would using WPA2 possibly improve the situation?

---

### Post by imrazor on 2010-01-18
I'll just post a follow up in case anyone ever finds this. The key to getting WPA/WPA2 working properly was this page covering basic hostapd configuration:

[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

Setting up a barebones hostapd config seems to have done the trick. Now on to PPPOE...

---

### Post by imrazor on 2010-01-24
I thought I'd post a followup to this, since someone may run into this one day. To resolve the OS X connect problem, I had to uncomment this line and set it like so in /etc/hostapd/hostapd.conf:
 
eapol_version=1
 
Setting it thusly allows OS X clients (including Leopard, Snow Leopard and iPhone 3.1.2) to connect. I've been told that there's no functional difference between v1 and v2 of EAPOL, but that some "old" OS's don't implement it properly. Whatever works...
 
I also ran into another issue with the b43 driver in that it was very unstable. The connection would stay up for an hour or so, then just die. In debug mode, the logs showed that hardware WPA encryption would just die with no explanation. After a good bit of experimentation, I found that disabling QoS support in the b43 driver made things much more stable, by an order of magnitude. This can be accomplished by adding the following line to /etc/modules:
 
b43 qos=0 verbose=3
 
qos=0 turns off QoS support, and verbose=3 turns on debugging output in /var/log/kern.log. You can probably safely drop the verbose parameter altogether.
 
Now on to PPPoE...I think I'll make another post about that and talk to myself some more. :)

---

### Post by SephiRok on 2010-04-28
Many thanks, qos = 0 was a life saver.

---

### Post by ShadowWraith on 2011-03-03
Kudos to you for the qos-0 fix! My b43 driver was giving me problems for a while and this totally solved them!

---

