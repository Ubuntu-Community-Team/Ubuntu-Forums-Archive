---
title: "Connecting to unsecured network from command line"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by Dastweeper on 2013-08-08
Hello,
I'm trying to get my system to connect to my home wireless network. Crazy, huh? It's unsecured, and my iwconfig shows my wireless card, (wlan0 has a bunch of details) but I can't seem to get to my network. I'm running XBMCbuntu, which is just built on lubuntu, but that means I don't have access to a standard Networked GUI; just a "network connections" dialog which doesn't do much.

I tried following the instructions [here]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo"), but lubuntu 12.04 is not recognizing any of the commands, and [here]("http://ubuntuforums.org/showthread.php?t=1796412"), [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections"), and [here.]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections") Every time I use iwconfig to set my network settings, it appears to work, but I have no connection.

I cannot for the life of me figure out what's going on. My network is functional on other systems,  I've correctly set the essid via command line, but it's just not playing ball.

I'm using a WG113v3 wireless card if it helps.

I thnk you for your patience.

---

### Post by prodigy_ on 2013-08-08
For unsecured networks you shouldn't really need anything special. Assuming that your wireless AP automatically assigns IP addresses (via DHCP) you need to add the following lines to the **/etc/network/interfaces** file:```
auto wlan0
iface eth0 inet dhcp
       wireless-essid NETWORK # replace NETWORK with your actual Wi-Fi network name
       wireless-mode Managed # assuming you use access point or Wi-Fi router
```
then open terminal and type ```
sudo ip link set wlan0 up
```

If you'll get any error, post the output here.

---

### Post by Dastweeper on 2013-08-08
Drat. I was able to easily do that, but nothing happened. No error, nothing.

---

### Post by prodigy_ on 2013-08-08
Try ```
ip addr show
``` What does it say?

---

### Post by Dastweeper on 2013-08-09
Hoo boy. Gonna have to type it in manually:
```
lo: <LOOPBACK, UP, LOWER_UP> mtu 16436 qdisc noque state UNKNOWN
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host
valid_lift forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 100 link/ether 00:1b:b9:53:1c:ce brd ff:ff:ff:ff:ff:ff
3: wlan0:<NO-CARRIER, BRODCAST, MULTICAST, UP> mtu 1500 qdisc pfifo_fast state DORMANT qlen 1000 link/ether 00:22:3f:f8:20;7b brd ff:ff:ff:ff:ff:ff
```

---

### Post by prodigy_ on 2013-08-09
Oh yeah, you also need to specify Wi-Fi network name in **/etc/network/interfaces**. Sorry I forgot to mention that. Edited my [earler post](http://ubuntuforums.org/showthread.php?t=2166351&p=12750584&viewfull=1#post12750584).

---

### Post by Dastweeper on 2013-08-09
Thanks. I did, but still nada. Can't connect, and ip addr show gives the same output.

---

### Post by Dastweeper on 2013-08-09
Oh dear. Anyone know anything else I can try?

---

