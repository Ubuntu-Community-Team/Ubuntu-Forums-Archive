---
title: "Connecting to wireless via command line"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by D_style on 2010-06-21
Hello all,

I have setup my wireless card via ndiswrapper and I can see that if I perform an iwconfig that the card is wlan0. 

```
wlan0     IEEE 802.11g  ESSID:off/any
             Mode:Managed  Frequency:2.412 GHz  
               Access Point: Not-Associated
          Bit rate:54 Mb/s  Tx-Power:10 dBm  Sensitivity:0/3
          RTS thr:off  Fragment thr:off
          Encryption key:off
          Power Management:off
```

Also if I input the command iwlist scan I get an output of all the wireless devices in the area. On that list is my device with the following properties:

```
Cell 04 - Address: xx:xx:xx:xx:xx:xx
          Essid:"2wire345"
          Protocol: IEE 802.11b
          Mode: Managed
          Frequency 2.462 GHz (channel 11)
          Quality: 53/100  Signal level:-62 dBm  Noise level:-96 dbm
          Encryption key:on
          Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 
                    9 Mb/s; 12 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
          Extra:bcn_int=100
          Extra:atim=0
          IE: WPA Version 1
              Group Cipher : TKIP
              Pairwise Ciphers (1) : TKIP
              Authentication Suites (1) : PSK
```

I have attempted to connect with the router but I can't get any connection.  I know the password is: ########## (10 digits long) but for the life of me I can't get it to work via command line.

Thanks

MT

---

### Post by D_style on 2010-06-23
bump... i tried using the wpasupplicant and I am still not having any luck!  ANY help would be great!!! On my other computer I have setup the gnome desktop and configuring that was easy... This is way harder!

---

### Post by mfernandez on 2010-07-20
Were you able to get your wireless connection working?  If so, please post what you had to do to make it work.  Thanks.

---

