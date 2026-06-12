---
title: "problem running aircrack-ng on ubuntu 12.04"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by vinit.tiwari2012 on 2013-03-20
Hi,

I am having a dell inspiron laptop and I have installed ubuntu 12.04 on it. I am trying to use aircrack on my system but not able to do so.
Here is what I have tried so far:
```

# iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11abg  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 04:18:0F:9B:38:99   
          Bit Rate=54 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

So eth0 is what the interface I have for wireless card. So I tried following command then
```
# airmon-ng


Interface    Chipset        Driver

eth0        Unknown     wl - [phy0]


```

Also I forgot to mention
```

#rfkill list
root@vinit:~# rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Then I wrote

```
# airmon-ng start eth0
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
5468    avahi-daemon
5469    avahi-daemon
5471    NetworkManager
5630    wpa_supplicant
5633    dhclient
Process with PID 5633 (dhclient) is running on interface eth0


Interface    Chipset        Driver

eth0        Unknown     wl - [phy0]mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)
```

So I tried killing all the affecting processes using ```
airmon-ng check kill
``` which killed all the processes but they again got restarted automatically. So somewhere over internet I found I can use the ```
airodump-ng on mon0 
```since that is started in monitor mode. But it didn't work. also I tried to use airodump-ng on eth0 as well but it is also failing.

```
# airodump-ng eth0
ioctl(SIOCSIWMODE) failed: Operation not supported

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth0 <#>'
Sysfs injection support was not found either.


```

&

```
# airodump-ng mon0
Interface mon0: 
ioctl(SIOCGIFINDEX) failed: No such device


```


Please help me over in using aircrack. Thanks

---

### Post by Stonecold1995 on 2013-03-21
You'll probably be better off using Kali Linux instead if you're planning on using aircrack.

[http://www.kali.org/](http://www.kali.org/)

---

### Post by wildmanne39 on 2013-03-21
Hi, this topic is not supported on the ubuntu forum so it has been closed.

Your best option is to try the backtrack forum.

---

