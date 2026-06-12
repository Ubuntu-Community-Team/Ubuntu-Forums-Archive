---
title: "Cracking WEP"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Falc7 on 2010-05-07
I am following a tutorial on how to crack WEP (for educational purposes only), here are the 4 commands i've followed so far:

```
apt-get install aircrack-ng

Ifconfig wlan0 down

airodump-ng --showack wlan0

airodump-ng -w First --showack --berlin 3000 --bssid 00:22:15:23:6E:E2 -C 11 wlan0
```

I've changed this bit ```
00:22:15:23:6E:E2
``` to the one i want to crack, but i get this message:

```
jamie@jamie-ku:~$ sudo airodump-ng -w First --showack --berlin 3000 --bssid 00:21:27:1A:34:10 -C 11 wlan0
[sudo] password for jamie: 
Checking available frequencies, this could take few seconds.
Done.
No valid frequency given.

```

What am i doing wrong?

---

### Post by Iowan on 2010-05-07
There are plenty of other sites to get that information. This forum is the wrong place to ask for assistance with cracking - even for educational purposes only. (Imagine the opportunities for abuse...)

---

