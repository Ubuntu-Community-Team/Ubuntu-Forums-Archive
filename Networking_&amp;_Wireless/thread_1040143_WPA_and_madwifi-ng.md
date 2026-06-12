---
title: "WPA and madwifi-ng"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Sprut1 on 2009-01-15
I use the madwifi-ng driver, but that is incompatible with wpa_supplicant, what is the best solution to enable wpa support? Installing another driver and switching between them seems messy in my opinion, I read that its possible to compile the wpa_supplicant source with the madwifi-ng driver making it compatible. But don't know if this will work, anyone tried this?

Any thoughts appreciated.

---

### Post by Sprut1 on 2009-01-16
Bump.

I still have issues, no one use wpa? :)

---

### Post by Sprut1 on 2009-01-17
I've read some articles and found out that this shouldn't be much of a problem, but thats normally not the case. I installed the latest madwifi drivers for my atheros card. Interfaces are up and everything seems to be working perfect. Then I do:

```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i ath2 -D madwifi
```

Then I get:

```

Trying to authenticate with essid "my essid"
Authentication with 00:00:00:00:00:00 timed out.

```

This loops forever, I've tried pursuing this bug on google, but I can't find anything useful. I'm surprised it should be such a hassle just to get WPA wireless networking when my WEP wireless worked perfectly. Anyways.. this is the last attempt...cheers

---

### Post by Ryuhayabusa on 2009-05-14
hey man,

did wpa_supplicant -h put out madwifi i.e do you have it compiled in?

i don't on my machine. I am thinking about trying to compile it in.

---

