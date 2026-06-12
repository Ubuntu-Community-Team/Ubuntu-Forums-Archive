---
title: "need help troubleshooting networkmanager and VPN"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2012-04-19
I am having an issue with openconnect VPN and networkmanager. Attempting to connect via the nm-applet fails, and the only thing I have found in the syslog is 

```

Apr 19 08:13:43 Chronos NetworkManager[878]: <info> Starting VPN service 'openconnect'...
Apr 19 08:13:43 Chronos NetworkManager[878]: <info> VPN service 'openconnect' started (org.freedesktop.NetworkManager.openconnect), PID 3537
Apr 19 08:13:43 Chronos NetworkManager[878]: <info> VPN service 'openconnect' appeared; activating connections
Apr 19 08:13:46 Chronos NetworkManager[878]: <info> Policy set 'Auto CITYWIFI' (eth1) as default for IPv4 routing and DNS.
Apr 19 08:13:51 Chronos NetworkManager[878]: <info> VPN service 'openconnect' disappeared

```

Not exactly helpful, and I am not sure how to get any more useful data.

I can run opennconnect as sudo from the command line, and it connects fine.  I have also verified that I am part of the netdev group.

Thanks,
-J

---

### Post by miatawnt2b on 2012-04-24
bump

---

### Post by excetara2 on 2012-04-27
Think there has been some sort of regression in the nm-applet or elsewhere. I have seen another with this issue on 11.10. I have it on 10.04 and you as well. I would say post a bug report if you have time. I believe it might be one or I will post one soon because going out of town if I haven't heard that you have already.

---

