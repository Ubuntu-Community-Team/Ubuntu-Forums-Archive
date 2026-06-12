---
title: "some wifi q's"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-01-28
1. Hey I was mucking around with airemon-ng

i now have these  extra mon0 when i run iwconfig

how to i get rid of them?

2. Why does wlan0 list ESSID:off/any
   and Access Point: Not_associated

see code two



```
adam@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon0      IEEE 802.11bg  Mode:Monitor  Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon1      IEEE 802.11bg  Mode:Monitor  Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon2      IEEE 802.11bg  Mode:Monitor  Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon3      IEEE 802.11bg  Mode:Monitor  Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off

```

```
adam@desktop:~$ iwlist accesspoints
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

wlan0     Interface doesn't have a list of Peers/Access-Points

mon0      Interface doesn't have a list of Peers/Access-Points

mon1      Interface doesn't have a list of Peers/Access-Points

mon2      Interface doesn't have a list of Peers/Access-Points

mon3      Interface doesn't have a list of Peers/Access-Points

```

---

### Post by thefasterblueone on 2011-01-28
1. To get-rid-of the extra mon0 try

```
airmon-ng mon0 stop
```


2. you are not connected to a network, "Not-Associated".


Instead of  

```
iwlist accesspoints
```

try

```
iwlist scan
```

---

### Post by adduds on 2011-01-29
thank you both worked

although i had to 

sudo airmon-ng stop mon0 etc...

but ty :)

---

