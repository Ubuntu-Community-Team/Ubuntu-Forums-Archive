---
title: "ubuntu 11.10 ethernet problem"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by gobprasad on 2012-02-25
hi frnds....
   I was also struggling from ethernet not working, cable unplugged problem in latest Linux distributions . i installed the r8168 driver but after restart it wont work. I installed different linux distributions like ubuntu 11.10, Linux mint 12, fedora 16. but the problem remains the same.Then i realize what actually wrong. its not the driver or kernel of linux. its the ethernet cable that i was using. it was 100Mbps cable and in our institute the LAN has recently upgraded to 1Gbps. The Linux driver after consulting the DHCP server found 1Gbps connection speed but cable is not supported so its gave error message of cable unplug. after this i brought 1Gbps cable from market, and guess what everything is working perfect. No issue at all. No need to driver install or anything else. Just plug the cable and ur linux distribution is work with no issue even with r8169 driver which is default in latest distributions.

---

