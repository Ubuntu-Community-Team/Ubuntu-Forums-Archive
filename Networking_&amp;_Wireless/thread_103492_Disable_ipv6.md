---
title: "Disable ipv6"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by Sanix on 2005-12-14
How can I disable ipv6? When I tried to disable it, I got an error, which means "currently used".

---

### Post by 23meg on 2005-12-14
In /etc/modprobe.d/aliases change the line ```
alias net-pf-10 ipv6
```to ```
alias net-pf-10 off
```

---

### Post by jml on 2005-12-14
Lambert posted this link in another message thread. 

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Near the end of the document there are instructions on how to disable the app.

Joe

---

