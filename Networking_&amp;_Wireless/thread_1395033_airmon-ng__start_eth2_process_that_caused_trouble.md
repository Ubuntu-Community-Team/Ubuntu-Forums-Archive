---
title: "airmon-ng  start eth2 process that caused trouble"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by bankaitech on 2010-01-31
[FONT=monospace]
[LIST=1]
[*]coolroot:~$ sudo airmon-ng start eth2
[*] 
[*] 
[*]Found 5 processes that could cause trouble.
[*]If airodump-ng, aireplay-ng or airtun-ng stops working after
[*]a short period of time, you may want to kill (some of) them!
[*] 
[*]PID     Name
[*]985     NetworkManager
[*]1000    avahi-daemon
[*]1001    avahi-daemon
[*]1149    wpa_supplicant
[*]10643   dhclient
[*] 
[*] 
[*]Interface       Chipset         Driver
[*] 
[*]eth2            Unknown                 wl (monitor mode enabled)
[/LIST]
can someone tell me what's wrong? i got my eth2 monitor mode enabled....not only this got problem also on my wireshar eth2 is detected but now packets are captured......i spent 3hrs but no packets....using eth2.....help is much appreciated. thanx
[/FONT]

---

### Post by milton1 on 2010-01-31
these are network processes that do not play well with airmon. disable them, run aircrack (only on networks you have permission to test), then re-enable them either by hand or by a quick reboot.

---

### Post by bankaitech on 2010-01-31
bro, mind if u'll show my the process? i'm quite new to ubuntu...still a newbie....just a step by step command on howto and it would be fine. thanx bro.

---

### Post by milton1 on 2010-01-31
```
sudo kill -9 <PID>
```

---

