---
title: "Automatic WiFi connect at boot"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by sprince09 on 2009-05-01
Hi all,

What I'd like to do is set up my laptop so that when I boot it up, it will automatically try and connect with the strongest available wifi access point. The network I am trying to connect to has multiple AP's with the same ESSID, so I have to connect via MAC address. I've tested out the following running from a root shell in recovery mode:

ifconfig ra0 up
iwlist scanning
*read mac address of AP with strongest signal*
iwconfig ra0 ap xx:xx:xx:xx:xx
dhclient ra0

This connects my laptop to the network just fine (ra0 is my wireless device). 

I'd like to automate this process so that I can access my laptop via ssh without having to logon, specifically so that I can reboot it without having to worry about loosing my ssh connection for more than a few minutes. I've done a few simple startup scripts before, but I'm not sure how to have bash read the strongest wifi AP signal and grab the corresponding MAC address. Any hints?

---

