---
title: "Problems with Atheros,  AzureWave AW-NE785,  168c:002b"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by txepkine on 2013-01-13
Hi.
I'm sorry for my English.

I have problems with an  Atheros wireless card ( AzureWave AW-NE785, 168c:002b) in 12.04 LTS. I have looked the forums and some people have very similar problems (really slow connection and/or stop without disconnection from AP). I have work with some suggestions I have seen in the forum (nohwcrypt as kernel parameter, power off in iwconfig) without success.
But then, I realize that I only have this problems with one router (only works in b/g mode) but I have not in two diferent b/g/n routers. The " bad one"  (Zyxel P660) It is a very usual router in Spain some time ago because it was sold by defect by the "best" internet provider.
So the problems persist, but I think it could be a useful information for somebody.
I tried to modify the modulation in iwconfig, trying to force my card to work in b/g mode but iwconfig says this option in not possible to do (I think the module ath9k does not allow it).
For more references, I have a usb wireless card that works with the same drivers for usb devices (ath9k_htc).  I have the same problem that in the previous case (pci card), no problem with n routers but a lot with Zyxel. I have not tested with another b/g router, I'm sorry

If somebody can help thanks, and if somebody can use my information it will be beatifull.

Thanks a lot.
Txepkine.

---

### Post by praseodym on 2013-01-13
Hi,

the drivers ath9k and ath9k_htc are different. Please show:
```

grep ath9k /etc/modprobe.d/*
iwconfig
dmesg | grep ath9k
```
Firmware of the Zyxel router is up-to-date? Tried pure WPA2-AES (CCMP) encryption?

---

### Post by txepkine on 2013-01-14
Hi.

Thanks for your help.

I have updated my firmware but it was impossible for some unknown reason. As you say it was possibly important, I tried it again. I found in a forum that my router (Zyxel p-6600-HW-D1) had been modified by the internet service provider that sold it .  As a consequence, it uses a modified firmware. I uploaded it and all seems to be ok, I have to wait some time to confirm it, but it looks ok.....

Anyway, I show you the output you ask:
  
jordi@jordi-1015CX:~$ dmesg | grep ath9k
[   14.726258] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.726283] ath9k 0000:02:00.0: setting latency timer to 64
[   14.884632] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.889063] Registered led device: ath9k-phy0

jordi@jordi-1015CX:~$  grep ath9k /etc/modprobe.d/*
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1

jordi@jordi-1015CX:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksys"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:49:95:4C:9D
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:82   Missed beacon:0

eth0      no wireless extensions.


Thanks a lot.

---

### Post by praseodym on 2013-01-14
Please use the code tag ('#'-button, when the text is marked). Otherwise we will see smileys.

Only for this one:

```
grep ath9k /etc/modprobe.d/*
```
plus:

```
sudo iwlist scan
```

---

### Post by txepkine on 2013-01-14
Hi.

I think it's ok. No problems since 2-3 hours ago!
I'm sorry for the smiles...., here they are:

```
grep ath9k /etc/modprobe.d/*
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1

sudo iwlist scan

.....
wlan0     Scan completed :
          Cell 01 - Address: 00:13:49:95:4C:9D
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005d05a772
                    Extra: Last beacon: 12217664ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
.......

```Thanks.

---

