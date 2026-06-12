---
title: "internet on ubuntu way too slow vs Windows 7"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by princeofnam on 2012-07-10
I've been switching between Windows 7 and Kubuntu and the difference in speed and connectivity is ridiculous.  For one I keep getting intermittently disconnected from my home wireless on Kubuntu. (for anyone who specifically uses Kubuntu do you know why KDaemon keeps asking for access to my kdewallet as well as why I keep getting prompted for a "secrets" password that is neither the wifi password or my kubuntu pw?) I had similar bouts of disconnectivity a few months ago when I ran Ubuntu minus the kdewallet issues.  The connection is also noticeably slower.  Not sure how to resolve this.

---

### Post by Kirk Schnable on 2012-07-13
It would help to know which kernel version you're running, and what networking hardware you have. 

Please post the output of:

```
uname -r
```

```
lspci
```

Kirk

---

### Post by princeofnam on 2012-07-13
I actually figured it out.  I was using the proprietary driver for the Broadcom 4313 adapter.  Turns out that was a terrible mistake so I switched over to the open version.  Everything else, e.g. kernels, was up to date.

---

### Post by Kirk Schnable on 2012-07-13
> **princeofnam said:**
> I actually figured it out.  I was using the proprietary driver for the Broadcom 4313 adapter.  Turns out that was a terrible mistake so I switched over to the open version.  Everything else, e.g. kernels, was up to date.

Glad you got that sorted out.  You should update your thread subject to indicate it's been solved.

Kirk

---

