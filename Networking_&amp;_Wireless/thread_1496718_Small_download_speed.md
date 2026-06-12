---
title: "Small download speed"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by UT8F on 2010-05-29
Hi,
I have a problem with Ubuntu 10.04LTS. I have 5mbits internet connection on wireless. When I downloading somethink over transmission, download speed is about ~500KB/s. But if i try to browse internet at the sime time, or download another package with browser, after some time my interned speed goes down. I mean from 500KB/s its become only ~100KB/s. Not only on torrent, but global. I mean on web browser too. And its not go up. Helps only when I reconnect my internet connecton. I mean disconnect from wifi network, and connect it again. It's OS problem, because on windows everythink ok. Sou where is the problem?

P.S. Sorry for my bad english.

---

### Post by alexelprogramador on 2010-05-29
> **UT8F said:**
> Hi,
I have a problem with Ubuntu 10.04LTS.


hello

good o.s. :)


 
 > I have 5mbits internet connection on wireless.


 When I downloading somethink over transmission, download speed is about ~500KB/s.



with that type of mb connection you have enought speed to connect and to do everything you want.



>  But if i try to browse internet at the sime time, or download another package with browser, after some time my interned speed goes down.


I think you have a poor connection

What i want to mean with that, is that the strength of the signal is poor 


>  I mean from 500KB/s its become only ~100KB/s. Not only on torrent, but global. I mean on web browser too. And its not go up. Helps only when i turn off and turn on wifi again. 


It's OS problem, because on windows everythink ok. Sou where is the problem?

ok

if you type:

sudo iwconfig

pleasse, write what happens and public it on this post.


In my case, I have a good connection 92% of 100% maximun strength

```



lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"JAZZTEL_E1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:52:D0:C5   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:4536-3436-3830-4330-3233-3645-31
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

virbr0    no wireless extensions.



``` 


> Link Quality=64/70  Signal level=-46 dBm  Noise level=-88 dBm

It wants to mean that, if 70 is the 100% of the connection, I had 64 of this.

the signal level is better when the number is bigger

> P.S. Sorry for my bad english.

I have worstest english :P

---

### Post by UT8F on 2010-05-29
```
ut8f@ut8f-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"DLink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:5A:52:A1:3F   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Eam, At the same signal level I got 500KB/s in Windows.

---

### Post by UT8F on 2010-05-30
I found that there is no mether I'm surfing or not, after ~30min. of intensive downloading, when open only download program, download speed drops anyway. Where is the problem?

---

### Post by UT8F on 2010-05-31
Yap, It's ubuntu problem. I have reinstalled ubuntu, everythink worked fine, but when I installed newest updates, the problem showed up again. What I should to do?

Please, help me with this messup.

---

