---
title: "b43 driver: Aircrack-ng works in arch but not in ubuntu?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by schef on 2009-07-22
When i'm in ubuntu and install the same driver that i have installed in arch for my bcm4311 wireless card i experience some problems..

I noticed that the name of my wifi card in arch is wlan0 while in ubuntu is eth1. So when i try to start Airmon-ng by typing

```
sudo airmon-ng start eth1
```i get this message: 
> Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)So it says the monitor mod is enabled but it didn't create extra device mon0 like in arch.
And when i try to start Airodump-ng i would usualy write ```
sudo airodump-ng mon0
```and everything worked fine but this time mon0 didn't exist so i wrote ```
sudo airodump-ng eth1
```but then i have gotten this error > ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.I was reading all over the google and tried all kinds of drivers but it didn't matter.
Does anybody has any idea?

---

### Post by schef on 2009-07-22
I'v found the anwser: [http://ubuntuforums.org/showthread.php?t=1140607&highlight=airodump-ng+dv2000](http://ubuntuforums.org/showthread.php?t=1140607&highlight=airodump-ng+dv2000)

The problem was that i still didnt disable the default driver in System -> Administration -> Hardware Drivers.
So when i disabled it worked..my wifi card was renamed into wlan0 and it worked..

---

