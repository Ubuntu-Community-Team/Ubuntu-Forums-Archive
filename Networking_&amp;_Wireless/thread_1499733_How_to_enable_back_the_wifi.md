---
title: "How to enable back the wifi?"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by arielsegal on 2010-06-02
I used to have no problem with the wifi on my netbook, but after a friend played around with it the wifi is disabled.
I gathered some info, and I hope you can help me.

```

ariel@segal:~$ sudo -i
[sudo] password for ariel: 
root@segal:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@segal:~# 
root@segal:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:23:4e:34:bf:bd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@segal:~# 

```

---

### Post by linux-hack on 2010-06-02
And what did your friend do exately to your wifi ? Did you reboot ? does it do the same after the reboot ?

did you try > sudo ifconfig wlan0 up

---

### Post by arielsegal on 2010-06-02
I think he put the wifi in monitor mode. I did reboot the system since then.
I tried: ifconfig wlan0 up
but it didn't work.

---

