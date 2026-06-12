---
title: "Aircrack &amp; WEP - what am I missing?"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-01-31
I've been tinkering with aircrack and my wireless router. I set the security to WEP and have my wife connect while I do my thing.

Here's what I'm doing:

[LIST]
[*]Use airmon-ng to create a new ath0 interface in monitor mode
[*]Use airodump-ng to monitor the traffic to the AP and write packets to a saved .cap file
[*]use aireplay-ng to test injection and deauthenticate the client and capture the 4-way handshake
[*]use aircrack-ng with the .cap file(s) to obtain the key
[/LIST]
Now, once all the aircrack business is done, I get rid of the ath0 device in monitor mode```
sudo airmon-ng stop ath0
```create a new ath0 device```
wlanconfig ath0 create wlandev wifi0 wlanmode managed
```then issue the following commands```
iwconfig ath0 essid "XXXXXXX"
``````
iwconfig ath0 ap XX:XX:XX:XX:XX:
``````
ifconfig ath0 192.168.1.26 netmask 255.255.255.0 up
```and finally ```
route add default gw 192.168.1.1
```followed by```
echo 192.168.1.1 >> /etc/resolv.conf
```

Now when I enter iwconfig into my terminal, I show that I have all the right entries - i.e., the essid, ap mac address, key, channel, and everything else is right.

But I'm still not connected! I can't ping the router, I can't ping the other computer that I know is on the network, and I certainly can't do anything else.

Am I missing a step? Am I not understanding the process here?

Anyone care to show me the error of my ways?

---

