---
title: "Alternating use of eth0 and eth1"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by BertN45 on 2012-01-07
I have only one b44 Ethernet interface on my laptop and one b43 WiFi interface. I disable the WiFi when I am at home and only use the wired connection.

One time the wired interface is eth1 and after a boot it is eth0 and that keeps changing all the time.

It is annoying since I monitor the inteface using conky and in this way I sometimes miss the information about the loading of the eth0 or eth1 interface.

How can I force eth0 all the time?

Could it be caused by using both IPv4 and IPv6? I have switched off IPv6 (no support in USR8054 anyhow) and during a couple of boots it seems to use eth0?

I will watch it during the week.

---

### Post by jsra on 2012-01-08
Hi,
did you already try editing persistent rules for NICs?
```
sudo vim /etc/udev/rules.d/70-persistent-net.rules
```

jsra

---

### Post by BertN45 on 2012-01-08
I have booted the system now around 10 times and the problem disappeared after I disabled IPv6. So for me the problem is solved. However I do not think, it is correct that ipv4 and ipv6 can randomly assigns eth0/eth1, each time you boot. It looks like a  timing issue, who comes first. 

In my active days, we would go after it and solve it, but for open source I do not know. Is it useful, if I file a bug report?

---

