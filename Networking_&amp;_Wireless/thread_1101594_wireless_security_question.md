---
title: "wireless security question"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by nbo10 on 2009-03-20
Hi all,
I'm looking at /var/log/syslog and am seeing things that are making me suspicious. I'm connected through my wired network and a wireless point. I know my internet connection is going through the wired port, as I can see printers on the wired network. 

He is a snip of syslog

```

 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar 20 14:18:45 laptop2 dhclient: DHCPOFFER of 10.8.48.17 from 10.8.48.1
Mar 20 14:18:45 laptop2 dhclient: DHCPREQUEST of 10.8.48.17 on wlan0 to 255.255.255.255 port 67
Mar 20 14:18:45 -laptop2 dhclient: DHCPACK of 10.8.48.17 from 10.8.48.1
Mar 20 14:18:45 laptop2 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 


```

the ip address isn't part of my university domain. Whats going on? Should I be concerned? Thanks

I see this thread should be under the security board. Can it be moved?

---

