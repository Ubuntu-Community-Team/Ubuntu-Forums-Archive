---
title: "wireless issues"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by branflake42o on 2009-01-01
well it all started when the internet didnt get paid....now . my dual boot setup.. XP i had to renew my ip and bamm. I had inter once the bill was paid....but when I booted my ubuntu. still no internet...after I cycled agazillion times and renewed my ip. sudo dhclient -r
sudo dhclient
 I have signal..can see the router..but cannot seem to be able to connect to the router setup via firefox. ideas please..  not answers but ideas. please and thanx:)

---

### Post by MaindotC on 2009-01-01
Are you connected to the wireless network?  Use:
```

iwlist scan

```
Are you getting DHCP settings from the wireless access point?  Use:
```

ifconfig -a
cat /etc/resolv.conf

```

---

### Post by superprash2003 on 2009-01-01
are you able to ping router?

---

