---
title: "Cannot connect to networks with WEP"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by imafatmess on 2009-06-08
I am trying to connect to my BT Home Hub with no success currently on my desktop (running intrepid). I can connect on my laptop however with no difficulties whatsoever. The main difference is that I am using a Linksys WUSB11v4 with the desktop which I know has many problems. I have the driver set up and running using ndiswrapper and I know it works as I can connect to my next door neighbors unsecured network and also to BTOpenzone (something which is with the BT Home Hub). I just cannot connect to the actual BT Home Hub network, which is WEP encrypted.

I have been trying to connect with the network manager with no success. If I enter static information instead of just it using dhcp, I can make it connect to the network, yet not the internet. Using dhcp, which is what my ubuntu laptop uses, it doesn't connect.

I would post ifconfig and iwconfig but because im using network-manager and it hasn't connected, I havent because these show little useful information. Heres iwlist wlan0 scan though:

```
david@david-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:68:06:7F:B5
                    ESSID:"BTHomeHub-988D"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 02:1D:68:06:7F:B6
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:09:5B:69:CA:A3
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

If you want any other info, I shall provide it for you :)

Thanks very much in advance, I really appreciate it :)

---

### Post by superprash2003 on 2009-06-08
have you tried various combinations for authentication type like 64bit,128bit etc..

---

### Post by imafatmess on 2009-06-08
I have. Anyway I would have thought it would be the same as with my laptop which is 128-bit...

---

### Post by imafatmess on 2009-06-08
anyone able to help?

---

### Post by imafatmess on 2009-06-08
I guess no then :(

---

