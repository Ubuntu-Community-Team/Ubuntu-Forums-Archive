---
title: "Network Issues"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by josmcc on 2010-02-04
Hi all. Just had something wierd happen all of the sudden. I can't get an IP address through DHCP, can set static on Wired, but not Wireless, when I set static on wired, I can't resolve DNS, except through a proxy(squid) located on my DNS Server (UBUNTU 7.10). Problem I'm having is with 9.10 on my laptop. I know it's not a server or router issue as my other PCs are running fine. Thanks in advance. Any ideas.

---

### Post by mhgsys on 2010-02-04
Why don't you just assign the dns settings manually?

You'll find the dns settings in your router settings.

---

### Post by superprash2003 on 2010-02-04
step 8 has a screenshot on how you can add dns servers manually on network manager [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by josmcc on 2010-02-04
Settings DNS manually doens't work for the wireless. It says it can't connect. It will work on wired, but only when I connect through the proxy.

---

### Post by josmcc on 2010-02-04
Thanks for the replies everyone. I ended up blacklisting fwcutter broadcom drivers and using ndiswrapper. I did run into a problem with ndiswrapper renaming the interface from wlan0 to wlan1. I had to use wicd network manager to probe wlan1 instead of wlan0 in properties. Thanks to everyone who contributed to the ndiswrapper sticky.
My own fault broadcom chipset 4309 I saw is still unstable

---

