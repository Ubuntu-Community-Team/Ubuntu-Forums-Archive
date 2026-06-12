---
title: "Can't connect to my school's wifi network"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by vo6 on 2011-04-30
Hi all, I just installed Ubuntu on my laptop and I found that I cannot connect to my school's wifi network while i have no problem connecting using windows. Also I can connect to my home's wifi network. The details of the wifi network are as follow:

SSID: Universities WiFi
Authentication: WPA
Data Encryption: TKIP
EAP Type: PEAP (EAP-MSCHAPv2)
Trusted Root Certification Authorities: Equifax Secure Certificate Authority
Server Certificate: 802.1x.hku.hk

Here is the instruction for setting up in windows xp:
[http://www.hku.hk/cc/home/networks/wifi/Uwifi/xp.html](http://www.hku.hk/cc/home/networks/wifi/Uwifi/xp.html)

I have downloaded the certifate required and put it in my home directory
and selected that .cer when setting up the connection
But I still can't connect to it, please help

---

### Post by vo6 on 2011-05-01
My laptop is a hp 2230s and its using intel wifi link 5100 
please help, thanks

---

### Post by vo6 on 2011-05-01
it seems that its a problem of ubuntu 11.04
i just tried 10.10 and it just worked

---

### Post by Megaptera on 2011-05-01
Glad to read that you solved it!

---

### Post by vo6 on 2011-05-01
well I don't think its solved in 11.04 right?
output from iwconfig wlan0
[HTML]wlan0     IEEE 802.11abgn  ESSID:"Universities WiFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[/HTML]

output from ifconfig wlan0
[HTML]wlan0     Link encap:Ethernet  HWaddr 00:1e:65:77:ce:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]

---

### Post by vo6 on 2011-05-02
i finally got it to work by uninstalling network-manager
and installed wicd

---

### Post by smo0th on 2012-03-08
thanks, this also helped me with my 11.10 O:)

---

