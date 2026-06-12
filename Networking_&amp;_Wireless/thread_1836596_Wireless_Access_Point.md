---
title: "Wireless Access Point"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by adhika on 2011-08-31
Hi guys,

In Windows, I can create an ad hoc computer-to-computer connection via WiFi (e.g. to my iPhone) and share the internet when my laptop is connected to the ethernet LAN cable. 

I wonder if it is possible to do the same in Ubuntu. I am using 10.04 LTS, 64 bit... If it is still possible to do so, can somebody show me the way?

---

### Post by adhika on 2011-08-31
Here is my detailed specs:

lspci returns:
```
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

ifconfig returns:
```
wlan2     Link encap:Ethernet  HWaddr 00:1e:65:6c:91:b6  
          inet6 addr: fe80::21e:65ff:fe6c:91b6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:576 (576.0 B)

```

iwconfig returns:
```
wlan2     IEEE 802.11abgn  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by spiky001 on 2011-08-31
I have set mine upto ad hoc. So you get internet onto laptop via eht0 cable from router? If you open network manager then select edit connections, select Wireless then ipv4 tab and set the method to share this connection with other computors

---

### Post by adhika on 2011-08-31
Yeap, I get internet via eth0. 
When you go to network manager, do you need to create a new wireless network? I tried using that method creating an ad-hoc SSID and change the ipv4 to 'shared to other computers' but I can't seem to find the SSID from my iphone... Did I do it wrongly?

---

### Post by spiky001 on 2011-08-31
ok on the laptop is the wireless connected to your adhoc network? I found that I have to conect that to the wireless network i created then it shows up on the other machines as well as my phone

---

