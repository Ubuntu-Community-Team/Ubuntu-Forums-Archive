---
title: "ntp issues on mythbuntu 10.04"
date: 2010-07-25
forum: Mythbuntu
---

### Post by BadPenny on 2010-07-25
I just built a Mythbuntu 10.04 box, and I am having strange issues. I installed ntp and ntpdate, and ntp is running:

```

ntp       2399  0.0  0.0   4400   864 ?        Ss   Jul22   0:01 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 108:112

```

However, unless I run either rdate or ntpdate on a regular basis (e.g. every 15 minutes), then the clock does not stay stable enough on this machine to record programs.

Suggestions?
--bp

---

