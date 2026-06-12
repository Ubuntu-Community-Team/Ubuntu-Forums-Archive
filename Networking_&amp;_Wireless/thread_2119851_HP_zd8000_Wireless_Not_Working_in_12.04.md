---
title: "HP zd8000 Wireless Not Working in 12.04"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by animall on 2013-02-24
Hi, I'm new to ubuntu/linux and a bit lost. I  just installed 12.04 on my old hp zd8000 laptop and really love it,  except for the lack of a wireless connection.


 There is a button that turns the wireless on and off (in windows)  that is not working at all and the system seems to not recognize the  wirelss card that is present Broadcom BCM 4318.


 I am new so I have no idea of how to proceed and would be most grateful for any help anyone out there can offer.


 Thanks very much in advance!

---

### Post by Hadaka on 2013-02-25
Hi, please do and post...

```
lspci -nnk | grep -iA3 net 
```

thanks.

---

