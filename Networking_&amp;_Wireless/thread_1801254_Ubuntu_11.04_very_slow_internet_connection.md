---
title: "Ubuntu 11.04 very slow internet connection"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by Araz Oner on 2011-07-10
Hi there, i'm political activist from non-democratic country Azerbaijan. I'm a filmer and also write screenplays. So, my government was able to control my pc and do some tricks when i was on windows. As far as i know with ubuntu it is impossible. 

But the internet connection is really slow and i dont know what to do. With windows its normal but when its ubuntu it reduces more than 2-3 times as i checked from speedtest.net and other sources. Sometimes it is really good and fast. But it is only sometimes. not everytime.

I already disabled ipv6 and did some other tricks but couldnt fix it.I hope i'll get help here.

Thank you in advance.

Laptop Model: Acer Aspire 5742G
Wireless brand: Intel Corporation 82801 Mobile PCI Bridge (rev a5) 
after i paste "$ iwconfig wlan0" i get this:
> lan0     IEEE 802.11bgn  ESSID:"(Home Wireless)"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:1F:AA:E7:4D:07   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1029  Invalid misc:2832   Missed beacon:0


---

### Post by jmoorse on 2011-07-12
Is the Windows PC on wireless too?

---

### Post by garvinrick4 on 2011-07-12
> Link Quality=32/70  Signal level=-78 dBm  
That is a very bad signal are you a bit of a distance from router?

What is card and driver you are using:
```
 lspci -nnk | grep -iA2 network 

```
> Bit Rate=54 Mb/s
This a "G" rate you have a "N" card, what is router set at in 2.4 ghz, G or N or mixed:

But the bad, bad signal strength in most likely your problem.

---

