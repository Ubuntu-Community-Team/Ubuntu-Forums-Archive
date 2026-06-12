---
title: "cannot bond wlan0 and ppp0"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Xavier Oddmon on 2008-12-30
I recently got a data plan for my cell phone (Sony Ericsson z750a, AT&T), and get HSPDA at home. It is slightly faster than my DSL connection. I have heard about bonding, and would like to try to bond the two connections to improve my internet speed. I have run into one stumbling block, however. Here are the steps I have taken:

```

sudo ifdown wlan0
sudo ifdown ppp0
sudo ifconfig bond0 192.168.1.100 up
sudo ifenslave bond0 wlan0
sudo ifenslave bond0 ppp0

```

Now, there is a problem. After taking ppp0 down, it is removed from the output of ifconfig. However, I cannot enslave ppp0 if I leave it up. Is there anything I can do to get around this?

Also, I figure it's worth noting that I *cannot* get the network manager to work with my phone, so i'm using the command wvdial, which works great.

---

