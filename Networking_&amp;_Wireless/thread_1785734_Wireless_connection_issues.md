---
title: "Wireless connection issues"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by krosswindz on 2011-06-18
I had a perfectly working wireless setup on my laptop which acts like a server for me. I upgraded to natty from maverick and I am having issues connecting to my wireless network.

When I do a ifup eth1

I get the following error
```

cat: /var/run/wpa_supplicant.eth1.pid: No such file or directory
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1

```

I am able to get my wireless working if I manually issue the following command

```

wpa_supplicant -s -B -P /var/run/wpa_supplicant.eth1.pid -i eth1 -D wext -C /var/run/wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf
dhclient eth1

```

I am wondering what could be the cause with if-pre-up.d/wpasupplicant script which is not setting up things for my wireless.
[/code]

---

