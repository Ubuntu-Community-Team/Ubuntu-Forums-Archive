---
title: "wireless recognition issue"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by thundaraptor on 2009-03-30
my wireless works fine.  the problem is that i has trouble seeing new wireless networks after it has already connected to one.  how do i deal with this?  thanks

---

### Post by golliwog on 2009-03-30
If you aren't seeing the new networks, I would recommend doing a manual scan from a terminal window.

```
sudo iwlist wlan0 scan
```

wlan0 of course is going to be whatever your active wireless card is.  You can find this using 

```
lspci
```

Just search for your wireless card... should say something like "Wireless lan controller"

This is of course assuming you were using the connection manager in the first place, and not a terminal.  :)

-g

---

### Post by thundaraptor on 2009-03-30
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

was written after the lpsci command  not sure how this fits with wlan0

---

### Post by golliwog on 2009-03-31
Oh, sorry about that, I meant lspci to confirm that it is recognized, but you get the actual device by doing an ```
ifconfig
```

Find the same card as you just mentioned and trying doing a scan!

ie.

```
cory@Ubuntu-Desktop:~$ sudo iwlist wlan0 scan
[sudo] password for cory: 
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:98:5E:DA
                    ESSID:"Davis"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level:-61 dBm  Noise level=-66 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000002460fbbb18c
                    Extra: Last beacon: 236ms ago

```

It'll have multiple Cells for different networks.

-g

---

### Post by thundaraptor on 2009-04-05
i tried this but getting the error message device does not support this function.  meaning?  

i got this message including other stuff off the ifconfig scan 

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-6B-EF-00-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256123 errors:0 dropped:0 overruns:0 frame:45542
          TX packets:17744 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:46085115 (46.0 MB)  TX bytes:2184876 (2.1 MB)
          Interrupt:19

---

### Post by golliwog on 2009-04-05
Are you able to plug that computer directly into the net?  I had to do that to get my wireless card drives to work.  8.10 recognized my card but wouldn't let me turn the card on.  When I got online, I auto-updated then restarted and it picked up the card and installed newer drivers that work perfectly.

---

### Post by thundaraptor on 2009-04-07
the wireless care works.  as long as i have just logged into the system it will pick up any wireless signal fine.  the problem is the subsequent situations where i need to log onto a wireless nework it doesn't see or connect to anything.  as if i had just suspended the system or hibernated, when i come back the system won't search or find active wireless connections.  this forces me to have to restart ubuntu evertime i want to log in to a wireless connection.

---

