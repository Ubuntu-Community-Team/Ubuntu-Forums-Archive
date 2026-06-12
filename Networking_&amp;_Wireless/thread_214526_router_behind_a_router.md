---
title: "router behind a router?"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by jimp180 on 2006-07-12
Is this possible? heres my scenario;
 I allready have a router, a smoothwall firewall router with a red/green/orange setup (red is internet, green is lan, orange is the dmz)I happen to like my smoothwall it has been functioning bullet proof for at least 3 years now with about 1 week of downtime caused in its entirety by last years hurricane evacuation. The only downside to the smoothwall is that it doesn't support wireless cards. recently I bought a laptop and so now I need wireless conectivity. I have built a Ubuntu box with 1 nic and a RT2500 chipset wireless card, I have the rt2500,ra0, configured in ad-hoc mode. I bridged eth0 and ra0 and this worked letting my smoothwall serve dhcp/dns to my laptop. The only problem is that for whatever reason this setup will not allow https trafic to pass to the laptop, wierd as it may seem apparently the bridge/rt2500 combination is flaky. What I would like to do is reconfigure the Ubuntu as a router for the wireless card, so I can route all traffic from the wireless network to my smoothwall. as it stands my lan uses the smoothwall for dhcp and a dns relay with its gateway (the smoothy green card) being 192.168.0.1 i also have dhcp set up on the orange side (dmz) which has the Ubuntu box and my voip and the gateway for this side (the orange card) is 192.168.2.1 

Is it possible to set up the ubuntu box to do this using shorewall or iptables, and does anyone have any tips on how to accomplish this?

---

### Post by tturrisi on 2006-07-12
may get some ideas here:
[http://www-128.ibm.com/developerworks/linux/library/l-wap.html](http://www-128.ibm.com/developerworks/linux/library/l-wap.html)
[http://tuxmobil.org/linux_wireless_access_point.html](http://tuxmobil.org/linux_wireless_access_point.html)
[http://www.enterprisenetworkingplanet.com/nethub/article.php/3463611](http://www.enterprisenetworkingplanet.com/nethub/article.php/3463611)

---

