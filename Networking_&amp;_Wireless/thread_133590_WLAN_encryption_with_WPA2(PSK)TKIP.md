---
title: "WLAN encryption with WPA2(PSK)/TKIP"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by Firyar on 2006-02-20
Hi everyone,

i have a little problem with my Hoary install on my Acer Extens 4100 laptop. I searched a lot in this forum and in the German Ubuntu forums, but did not find a solution for my problem. I downloaded and installed the appropriate Intel firmware, the IPW2200 driver and the IEEE80211 subsystem. Of course i have deleted the old modules with the "remove-old" scripts. But there is still a problem with the encryption:

When i deactivate encryption at all, the card is working fine and i have no problem at all. When i activate WPA2/TKIP in the [wpa_supplicant.conf]("http://lockfile.org/upload/wpa_supplicant.conf") and try to lauch

```
wpa_supplicant -d -i eth0 -c /etc/wpa_supplicant.conf -Dipw -w
```

i receive the following [output]("http://lockfile.org/upload/wpa_messages.txt").

I have loaded the following modules:

```
ipw2200               156488  0 
firmware_class          9472  1 ipw2200
ieee80211              38760  1 ipw2200
ieee80211_crypt         5760  5 ipw2200,ieee80211_crypt_ccmp,ieee80211_crypt_tkip,ieee80211_crypt_wep,ieee80211
```

Perhaps i am missing an important module or i forgot to specify the encryption...or ...or ...or. I am a bit confused and do not know what else to do :confused:

---

### Post by drakeoutlaw on 2006-02-20
To make sure you are using your newly compiled ieee80211 modules see the output of dmesg. Or look in /var/log/syslog. When you modprobe ieee80211 you will see the message showing the version of 80211 being loaded.

I had a similar problem. I discovered that the old 80211 modules were being loaded from a different directory under /lib/modules. You can also do a search for 80211 modules under the /lib/modules directory/<yourkernelversion>/

Good luck,
Drake

---

### Post by Firyar on 2006-02-20
[QUOTE=drakeoutlaw]To make sure you are using your newly compiled ieee80211 modules see the output of dmesg. Or look in /var/log/syslog. When you modprobe ieee80211 you will see the message showing the version of 80211 being loaded.

I had a similar problem. I discovered that the old 80211 modules were being loaded from a different directory under /lib/modules. You can also do a search for 80211 modules under the /lib/modules directory/<yourkernelversion>/

Good luck,
Drake[/QUOTE]

Thanks for your quick response. I have double-checked the modules, everything OK there. These are the modules built from the IEEE package, not the modules included in the kernel sources. But the problem still exists.

---

