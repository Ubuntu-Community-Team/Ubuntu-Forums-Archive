---
title: "Aircrack-ng Problem."
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Darkizzwow-.- on 2010-08-29
Hello everyone ! I have problem with my aircrack-ng.
```
ubuntu@ubuntu-laptop:~$ sudo -i
[sudo] password for ubuntu: 
root@ubuntu-laptop:~# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
2604    NetworkManager
2622    wpa_supplicant
2628    avahi-daemon
2629    avahi-daemon
11982    dhclient
Process with PID 11982 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Unknown         wl (monitor mode enabled)

root@ubuntu-laptop:~# airodump-ng -c 6 --bssid 00:23:8E:E5:8F:26 -w psk wlan0
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

```anyone can help me ?? Please be fast. Its urgent. THANK YOU.:)

---

### Post by bkratz on 2010-08-29
> **Darkizzwow-.- said:**
> Hello everyone ! I have problem with my aircrack-ng.
```
ubuntu@ubuntu-laptop:~$ sudo -i
[sudo] password for ubuntu: 
root@ubuntu-laptop:~# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
2604    NetworkManager
2622    wpa_supplicant
2628    avahi-daemon
2629    avahi-daemon
11982    dhclient
Process with PID 11982 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Unknown         wl (monitor mode enabled)

root@ubuntu-laptop:~# airodump-ng -c 6 --bssid 00:23:8E:E5:8F:26 -w psk wlan0
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

```anyone can help me ?? [COLOR="Red"]Please be fast. Its urgent.[/COLOR] THANK YOU.:)

Are you war-driving? You might go to the forums at
[http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)
Probably not get much help here since no one knows whether your activities are legal or not.

---

### Post by Darkizzwow-.- on 2010-08-29
And by the way... My wireless card is Broadcom. and i'm not war-driving. but i searching on net about 2 days and i'm borred. :( so i just wanna ask experts. Thx.

---

### Post by Iowan on 2010-08-29
**aircrack** experts would more likely be found on their [forum]("http://forum.aircrack-ng.org/") than this one. Feel free to use the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") to get thread re-opened.

---

