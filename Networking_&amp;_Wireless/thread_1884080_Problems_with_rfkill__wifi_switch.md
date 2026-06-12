---
title: "Problems with rfkill / wifi switch"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by runny6play on 2011-11-20
```
sudo ifup wlan0
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with a return code of 1
RTNETLINK answers: operation not possible due to RF-kill
Failed to bring up wlan0
```

```
rfkill list all
1: dell-wifi: wireless LAN
Soft blocked yes
Hard blocked yes

3: Wireless LAN
Soft blocked no
Hard blocked yes

```

Thing is my laptop doesnt even have a hard wifi switch...
Only a light...


So I'm a little lost on what I can do to solve this problem

---

### Post by collisionystm on 2011-11-20
It's probably on the keyboard. The FN key and a function key such as f4

---

### Post by runny6play on 2011-11-20
wow.... I feel really dumb... :redface: its been so long sense ive touched it i completely forgot that it existed.  I must of accidently turned it on when switching to one of the terminal logins
Thanks

---

