---
title: "Connecting a Kindle to an ad hoc network"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by The Midnight Coder on 2011-07-20
Hey,

I am trying to connect my Kindle via wifi using an ad hoc network but when I try connecting it says "Enterprise or peer-to-peer Wi-Fi networks are not supported". 

After looking on google, I figured that the connection needs to emulate a router. Does anybody know how I can accomplish this :confused:

---

### Post by shecky on 2011-10-29
This tutorial ssssort of works. Kindle can connect and all, but then the computer has no connection. Maybe I'm doing it wrong.

[http://code.google.com/p/quickanddirty/wiki/CreatingWirelessHotspotWithLinux]("http://code.google.com/p/quickanddirty/wiki/CreatingWirelessHotspotWithLinux")

---

### Post by shecky on 2011-10-29
Monkeyed with that tutorial a bit more and got both wired and wireless working. Here's my own config files and a script to make it be worky.

My router IP is 192.168.1.1 and my computer IP is 192.168.1.2.

**/etc/dnsmasq.conf:**
```
expand-hosts
domain=derplink.net
dhcp-range=192.168.1.50,192.168.1.150,12h
dhcp-option=option:router,192.168.1.2
dhcp-leasefile=/var/lib/misc/dnsmasq.leases
address=/virago.derplink.net/192.168.1.2
log-queries
log-dhcp
```

**/etc/hostapd/hostapd.conf:**
```
interface=wlan0
driver=nl80211
bridge=br0

country_code=US
ieee80211d=1

ssid=buttmunch
hw_mode=g
channel=6
wme_enabled=0

macaddr_acl=0
auth_algs=1
wpa=2
wpa_passphrase=PASSWORD
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

**/usr/local/bin/WirelessAP:**
```
#!/bin/bash
ROUTERIP="192.168.1.1"
COMPUTERIP="192.168.1.2"
WLANIP="192.168.0.1"

sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F
sudo iptables -X
sudo iptables -t nat -X
sudo iptables -t mangle -X

sudo ifconfig eth0 $COMPUTERIP
sudo ifconfig wlan0 $WLANIP

sudo route del default gw $ROUTERIP
sudo iptables -A FORWARD -o eth0 -i wlan0 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo route add default gw $ROUTERIP eth0

sudo service dnsmasq stop

sudo ifconfig eth0 down
sudo ifconfig wlan0 down

sudo ifconfig eth0 0.0.0.0 up
sudo ifconfig wlan0 0.0.0.0 up

sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 wlan0

sudo ifconfig br0 $COMPUTERIP up

sudo route add default gw $ROUTERIP

sudo service dnsmasq start

sudo hostapd /etc/hostapd/hostapd.conf

# Restore default after ctrl+c
sudo iptables -F;
sudo service dnsmasq restart
sudo ifconfig br0 $COMPUTERIP down
sudo brctl delbr br0
sudo service network-manager restart
```

After setting up the config files with your own values, run **sudo WirelessAP** to start stuff up. Hitting CTRL+C will restore it back to normal.

---

