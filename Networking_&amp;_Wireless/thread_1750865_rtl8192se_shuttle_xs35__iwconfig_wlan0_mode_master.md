---
title: "rtl8192se shuttle xs35  iwconfig wlan0 mode master"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by zaphod777 on 2011-05-06
Hey guys I was wondering if you could give me a little help. I have a Shuttle xs35gt running Ubuntu server 10.10. I want to try and configure it as a wireless router. It looks like maybe I can use the built in wireless adapter in AP mode but it doesn't allow me to set it in master mode.

the adapter is a rtl8192se
[http://218.210.127.131/products/productsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=230](http://218.210.127.131/products/productsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=230)

```
 Last login: Fri May  6 11:05:39 2011 from 192.168.1.1
xbmc@hal:~$ iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
wlan0     802.11bg  Nickname:"rtl8191SEVA1"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
xbmc@hal:~$ sudo iwconfig wlan0 mode master
[sudo] password for xbmc:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
xbmc@hal:~$
```

---

