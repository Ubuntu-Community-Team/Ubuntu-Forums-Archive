---
title: "Setting up my Wifi Hotspot with 3 cards"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by kamgos on 2012-09-11
I have 3 lancards install in my ubuntu 10.04 server
I want to confiure internet sharing and file sharing on eth1 for cable users and wlan0 for wireless users

Static ip 
eth0-192.168.1.1
eth1-10.0.0.15
wlan0-10.0.0.20

sudo vi /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


#The secondary network interfaces
auto eth1
iface eth1 inet static
address 10.0.0.15
netmask 255.0.0.0
network 10.0.0.0
broadcast 10.255.255.255

auto wlan0
iface wlan0 inet static
address 10.0.0.20
netmask 255.0.0.0
network 10.0.0.0
broadcast 10.255.255.255


I have use squid and dansguardian for internet configured

I have configure following in hostapd

etc/hostapd/hostapd.conf with WPA authentication options.

01	interface=wlan0
02	driver=nl80211
03	ssid=dontMessWithVincentValentine
04	hw_mode=g
05	channel=6
06	macaddr_acl=0
07	auth_algs=1
08	ignore_broadcast_ssid=0
09	wpa=3
10	wpa_passphrase=KeePGuessinG
11	wpa_key_mgmt=WPA-PSK
12	wpa_pairwise=TKIP
13	rsn_pairwise=CCMP

DHCP server also configured 

sudo vi /etc/dhcp3/dhcpd.conf

ddns-update-style none;
ignore client-updates;
authoritative;
option local-wpad code 252 = text;
subnet
10.0.0.0 netmask 255.255.255.0 {
# --- default gateway
option routers
10.0.0.15;
# --- Netmask
option subnet-mask
255.255.255.0;
# --- Broadcast Address
option broadcast-address
10.0.0.255;
# --- Domain name servers, tells the clients which DNS servers to use.
option domain-name-servers 10.0.0.15, 127.0.0.1, 192.168.1.1;
option time-offset
0;
range 10.0.0.21 10.0.0.30;
default-lease-time 1209600;
max-lease-time 1814400;
}

sudo vi /etc/default/dhcp3-server
INTERFACES="eth1 wlan0"

I have enable packet forwarding for IPv4 and IPv6
sudo nano /etc/sysctl.conf
    Net.ipv4.ip_forward = 1
    Net.ipv6.conf.all.forwarding = 1

    sudo nano /etc/rc.local

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

The client pc areable to receive internet sharing on eth1 and also dhcp address and ping the other network

from wlan to client pc are able to receive dhcp address but are not able to ping to 10.0.0.20 through which they are receivng dhcp address or any other pc in the network 
My firewall is also not enable

what can be the problem why the wireless lan users are not able to ping or communicate 

Thanks for your help in advance

---

