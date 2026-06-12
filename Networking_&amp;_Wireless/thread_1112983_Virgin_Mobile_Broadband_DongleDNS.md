---
title: "Virgin Mobile Broadband Dongle/DNS"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by purct on 2009-04-01
Hi,

I have just purchased a Virgin Mobile broadband dongle and am trying to config it on Ubuntu 8.10.  It seems to connect but I am unable to surf the net...I have checked the ifconfig & routing tables they are fine(and correctly updated with the DHCP addresses), however resolv.conf is not updated with DNS settings. The resolv.conf is updated fine when using my home broadband and when I vpn into work but not when using the dongle...does anyone have any suggestions on what is wrong? if not, can anyone tell me what the DNS settings should be?

Thanks

---

### Post by coutts99 on 2009-04-01
Try the opendns servers -:

208.67.222.222
208.67.220.220

---

### Post by superprash2003 on 2009-04-01
are you able to open [http://74.125.45.100](http://74.125.45.100)

---

### Post by purct on 2009-04-02
> **superprash2003 said:**
> are you able to open [http://74.125.45.100](http://74.125.45.100)

yes, because the issue is with DNS.   I use serveral different networks, so need to keep my DHCP & Dynamic updates to DNS. 

The initial problem has been resolved now....When I configured the new interface link in NetworkManager it replaced the symbolic link file(resolv.conf) with a new resolv.conf (thats not symbolic linked) so resolvconf failed to update the file.....I removed the /etc/resolv.conf and re-created the symbolic link. 

When I connect now, resolv.conf is updated with the DNS for the Mobile Broadband! however, it appears that I have another issue now..

When my Wireless Lan card is disabled/shutdown resolvconf fails to remove the eth1.NetworkManager file from /etc/resolvconf/run/interface.   the upshot is that when the new resolv.conf file is written (on connecting via Mobile Broadband) it includes the DNS settings from eth1 and then ppp0.  

On connecting and disconnecting of other interfaces resolvconf clears them up fine, but not for my Wireless LAN. I am now investigating why.   I think I need to look into the /etc/network/if-down.d/ script files to see if I can work out whats going on.

---

