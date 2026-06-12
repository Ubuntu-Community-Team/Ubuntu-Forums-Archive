---
title: "UNABLE TO SET AD-HOC(IBSS), MASTER, (iwconfig wlanX mode ad-hoc/master) MODES!"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by kinesis1 on 2011-06-07
root@hack:/home/k# iwconfig wlan1 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Device or resource busy.
root@hack:/home/k# iwconfig wlan1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.
root@hack:/home/k# 


I rely on ad-hoc mode to tether with my mobile phone. I rely on master mode to use Kismet wireless scanner. Why don't these features work? How do i get them to work? I had to remove Avahi Daemon  by renaming the binary, it was causing problems, i also had to rename dhclient to dhclient-broken, same with dhclient3->dhclient3-broken. For some reason I am forced to start wpa_supplicant before my wlan1 usb card even begins to work properly then I can't use the 'mode ad-hoc' change. Prior to wpa_supplicant, the mode ad-hoc change works but it cannot associate with any AP.


I normally use Slackware and don't run into these bastardizations of networking and the problems resulting thereof, but I am choosing Ubuntu because of it's better hardware support of this particular notebook. I'd like to get ad-hoc mode working so I can tether with my phone - any ideas? wpa_gui works, i just cannot connect to STA's that have 'ad-hoc' mode.

---

### Post by chili555 on 2011-06-07
> I rely on master mode to use Kismet wireless scanner.Why? On my system, Kismet runs in monitor mode, not master.> SET failed on device wlan1 ; [COLOR="Red"]Device or resource busy[/COLOR].This usually indicates that you need to bring the interface down first:```
ifconfig wlan1 down
iwconfig wlan1 mode ad-hoc
```

---

### Post by kinesis1 on 2011-06-07
Incorrect, I had tried that, and it did not work.

The fix:



```
root@hack:~# ip link set wlan1 down
root@hack:~# iwconfig wlan1 mode ad-hoc
root@hack:~# iwconfig wlan1
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Ad-Hoc  Cell: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@hack:~# iwconfig wlan1 essid goats
root@hack:~# iwconfig wlan1
wlan1     IEEE 802.11bgn  ESSID:"goats"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@hack:~# iwconfig wlan1 key s:xxxxxxxxxxxxxx
root@hack:~# iwconfig wlan1
wlan1     IEEE 802.11bgn  ESSID:"goats"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7xx5-xxxx-xxxx-4xx3-93x5-1337-69
          Power Management:on
          
root@hack:~# dhclient-broken wlan1
root@hack:~# ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.224.209) 56(84) bytes of data.
64 bytes from 74.125.224.209: icmp_req=1 ttl=51 time=128 ms
64 bytes from 74.125.224.209: icmp_req=2 ttl=51 time=131 ms
^C
--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2002ms
rtt min/avg/max/mdev = 128.797/130.325/131.853/1.528 ms
root@hack:~#
```

Also yeah, 'monitor' mode, not master. I haven't ran kismet in awhile.

---

