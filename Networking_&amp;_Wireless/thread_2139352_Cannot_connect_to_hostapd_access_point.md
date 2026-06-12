---
title: "Cannot connect to hostapd access point"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by pinguypuppy on 2013-04-26
I can successfully connect to the access point but cannot access the internet. Note that my computer is already behind a proxy and has the IP address 10.1.39.14.

My */etc/dhcp/dhcpd.conf:*

```
ddns-update-style none;
ignore client-updates;
authoritative;
option local-wpad code 252 = text;
option domain-name-servers
10.1.39.1, 8.8.8.8, 8.8.4.4;
 
subnet
10.0.0.0 netmask 255.255.255.0 {
# --- default gateway
option routers
10.0.0.1;
# --- Netmask
option subnet-mask
255.255.255.0;
# --- Broadcast Address
option broadcast-address
10.0.0.255;
# --- Domain name servers, tells the clients which DNS servers to use.
option time-offset
0;
range 10.0.0.3 10.0.0.220;
default-lease-time 1209600;
max-lease-time 1814400;
}
```

My *hostapd.conf*:

```
interface=wlan0
driver=nl80211
ssid=WiMax
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=interestingstuff
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

My *configuration script*:

```
#!/bin/bash
#Initial wifi interface configuration
export PATH=$PATH:/home/green/hostap/hostapd;
ifconfig $1 up 10.0.0.1 netmask 255.255.255.0
sleep 2
###########Start DHCP, comment out / add relevant section##########
#Doesn't try to run dhcpd when already running
if [ "$(ps -e | grep dhcpd)" == "" ]; then
dhcpd $1 &
read x
fi
###########
#Enable NAT
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface $2 -j MASQUERADE
iptables --append FORWARD --in-interface $1 -j ACCEPT

#Uncomment the line below if facing problems while sharing PPPoE, see lorenzo's comment for more details
#iptables -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

sysctl -w net.ipv4.ip_forward=1
#start hostapd
/home/green/hostap/hostapd/hostapd -dd /home/green/.hostapd.conf
killall dhcpd
```

---

