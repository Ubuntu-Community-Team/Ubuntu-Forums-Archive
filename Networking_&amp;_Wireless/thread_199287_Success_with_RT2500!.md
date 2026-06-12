---
title: "Success with RT2500!"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by yaidiot! on 2006-06-18
The Ralink Technology drivers work as advertised with my laptop. The only bit of funkiness (and this took me a week to figure out,) is each time I switch between wired and wireless networks I have to take the other interface down -- that is:

```
sudo ifdown eth0
sudo ifup ra0
```

or vice versa. The clue was seeing the system get a dhcp address but fail a ping.

Its a MSI MP54G4 ($20 @ newegg) working with WPA (AES). Hope it helps someone.

---

