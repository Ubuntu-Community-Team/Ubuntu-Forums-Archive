---
title: "aircrack-ng"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by hallve_revera on 2009-05-21
hii 
got a lil problem here
when i tried to run airmon-ng that i installed from source, i got this notification

Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
8319	avahi-daemon
8320	avahi-daemon
9071	NetworkManager
9083	wpa_supplicant


any explanation   ????
how do i kill the process and bring it back after using aircrack tool...???


thanks

---

### Post by dryphi on 2011-08-27
```
sudo service network-manager stop
sudo service avahi-daemon stop
sudo pkill wpa_supplicant
```

Should kill them all. This can be verified with:
"sudo airmon-ng check" and "sudo airmon-ng check kill"

To bring them back, try "sudo service network-manager start", which should bring back the others as well.

---

### Post by poolet on 2011-08-27
aircrack is an old program, and there are many error that you may find in the future... In my opinion donwload vmware and install backtrack on it.. And run it aircrack from there you will suprise with the results!!!!!

---

### Post by Iowan on 2011-08-27
> **poolet said:**
> aircrack is an old program,... and this is an old thread - now closed.

---

