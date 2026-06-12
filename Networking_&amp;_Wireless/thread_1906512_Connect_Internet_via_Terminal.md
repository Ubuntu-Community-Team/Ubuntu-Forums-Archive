---
title: "Connect Internet via Terminal"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by intelligence storm on 2012-01-09
Hi all,
I want to write a script that would connect to the Internet when it runs so I have to know how to connect the internet via Terminal.
I've read a lot of posts, threads,....etc over the Internet but nothing could help me #-o
As mentioned with this [thread  ]("http://ubuntuforums.org/showthread.php?t=1740726")it solved for him and I tried the same commands but still not solved :cry:
===================================================================================
well, I added the commands here to /etc/network/interfaces:
```
auto lo iface lo inet loopback  auto wlan0 iface wlan0 inet dhcp wpa-ssid mynetworkname wpa-psk mypassphrase
```but still the problem comes !!
it shows these messages:
```
No DHCPOFFERS received.
Trying recorded lease 192.168.1.100
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
```then how could I check if it connected or NOT ??

---

### Post by KrisDouglas on 2012-01-09
Hello,

Your system should remember the fact that it is connected to the internet when it boots.

The questions I need to ask are do you use WiFi, an Ethernet cable, or a USB modem to connect?

---

### Post by intelligence storm on 2012-01-09
It's WI-fi connection :)
Hmmm.....does that means if the script runs on other computer it does not work ??

---

### Post by chili555 on 2012-01-09
Is the interfaces file correctly formatted?```
auto lo
iface lo inet loopback

auto wlan0 
iface wlan0 inet dhcp 
wpa-ssid mynetworkname 
wpa-psk mypassphrase
```Is Network Manager removed?

You can check to see if you are really connected with:```
ping -c3 www.google.com
```

---

### Post by intelligence storm on 2012-01-09
Network-manger is not removed.
the format of file is correctly as you mentioned.
after write :
```
sudo ifdown wlan0 && sudo ifup wlan0
```
it tells:
```
ifdown: interface wlan0 not configured
```
but when type :
```
sudo ifup wlan0
```
it tells:
```
ifup: interface wlan0 already configured
```
!!!
The end of command run is :
```
No DHCPOFFERS received.
Trying recorded lease 192.168.1.100
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

---

### Post by chili555 on 2012-01-09
> Network-manger is not removed.Manual methods, that is, shell scripts, /etc/network/interfaces, etc. are very unlikely to work correctly as long as NM has a firm grip on your system. I can't do it and I know quite a bit about networking!

---

