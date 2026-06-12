---
title: "can't get wireless (atheros) into monitor mode"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by annoluce on 2010-03-22
Hi,
I can't get my wireless into monitor mode. 
I;m running ubuntu 9.1 karmic
It connects fine to wireless networks. 
But when i do: sudo iwconfig wlan0 mode monitor. I get: Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


I can only see wlan0 (wmaster0, eth0), not ath0 or wifi0 mentioned elsewhere, in wireshark.  
I only see my own ip and packets coming to and from that. 

my system tells me i have an atheros ar9285 chipset in place.

---

### Post by Alias1407 on 2010-03-22
> **annoluce said:**
> Hi,
I can't get my wireless into monitor mode. 
I;m running ubuntu 9.1 karmic
It connects fine to wireless networks. 
But when i do: sudo iwconfig wlan0 mode monitor. I get: Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


I can only see wlan0 (wmaster0, eth0), not ath0 or wifi0 mentioned elsewhere, in wireshark.  
I only see my own ip and packets coming to and from that. 

my system tells me i have an atheros ar9285 chipset in place.

I would install the aircrack-ng suite. It makes things a lot easier such as turning your card into monitor mode. First download it with a simple apt-get install....
```
sudo apt-get install aircrack-ng
```
Then you want to turn your wireless interface into monitor mode (for this example I'll use wlan0 but yours could be ath0)...
```
sudo airmon-ng start wlan0
```
And that's it.

For your wireshark problem I would try starting it in root e.g.
```
su
```
<enter password>
```
wireshark
```

---

### Post by fredo994 on 2011-01-21
I got the same problem and I have aircrack-ng and even then when I tried to switch to minitor mode in aircrack i get the same error:

wlan0			ath9k - [phy0]/usr/local/sbin/airmon-ng: 856: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)

fredo@fredo-laptop:~$ Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
please HELP

---

