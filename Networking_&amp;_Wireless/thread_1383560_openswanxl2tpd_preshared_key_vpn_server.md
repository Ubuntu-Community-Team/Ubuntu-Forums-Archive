---
title: "openswan/xl2tpd preshared key vpn server"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by kingjm on 2010-01-17
I am trying to setup a vpn server. I have found an easy to follow guide. However I can't seem to connect. I am looking to start over. I will write a guide in the wiki once this is complete as nothing there exists of this nature. please help

The base guide: [http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html](http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html)

My router IP is 192.168.0.1 with DHCP 192.168.0.100-253
My Ubuntu Server 192.168.0.100

Forward IPs to:
[INDENT]192.168.0.100 500,4500 UDP (ipsec)
192.168.0.100 1723 TCP (pptp)
Do not forward 192.168.0.100 1701 UDP (l2tp)
[/INDENT]
My Guide:

Install and Configure Openswan
[INDENT]
sudo apt-get install openswan
[I]No, do not enable Opportunistic Encryption
No, do not create a RSA public/private keypair
[/I]

sudo cp /etc/ipsec.d/examples/l2tp-psk.conf /etc/ipsec.d/l2tp-psk.conf

sudo nano /etc/ipsec.d/l2tp-psk.conf
Set 
```
left=192.168.0.100       #External Server IP
leftnexthop=192.168.0.1  #Gateway of Router
```

nano /etc/ipsec.conf
```
include /etc/ipsec.d/l2tp-psk.conf
```

nano /etc/ipsec.secrets
```
192.168.0.100 %any: "yourSharedPSK!"
```

sudo /etc/init.d/ipsec restart[/INDENT]

Install and Configure xl2tpd
[INDENT]sudo apt-get install xl2tpd

sudo nano /etc/xl2tpd/xl2tpd.conf
```
[global]
ipsec saref = yes
listen-addr = 192.168.0.100
auth file = /etc/ppp/chap-secrets

[lns default]
ip range = 192.168.0.210-192.168.0.219
local ip = 192.168.0.100

ms-dns 192.168.0.100   #ubuntu bind server
ms-dns 8.8.8.8         #Google DNS server

require-mschap-v2
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes
```

sudo cp /etc/ppp/options /etc/ppp/options.xl2tpd
sudo nano /etc/ppp/options.xl2tpd
Change *noauth* to *auth*.

sudo /etc/ppp/chap-secrets
```
#client	server		secret		IP addresses
username	l2tpd		"password"	*
l2tpd		username	"password"	*
```[/INDENT]

Install and Configure Pptpd [Working]
[INDENT]sudo apt-get install pptpd
sudo nano /etc/pptpd.conf
```
localip 192.168.0.100
remoteip 192.168.0.220-229
```

sudo /etc/ppp/options
```
ms-dns 192.168.0.100   #ubuntu bind server
ms-dns 8.8.8.8         #Google DNS server
```

sudo  /etc/ppp/chap-secrets
```
username pptpd password  *
```

sudo restart pptpd
[/INDENT]

sudo nano /etc/sysctl.conf
```
net.ipv4.conf.default.forwarding=1
```
This forwards traffic to outside

Sudo sudo arp --use-device --set 192.168.0.100 eth0 pub
This creates the arproxy 

That's all I got. Any Help Will be great. I will edit above to show the changes as people help to contribute.

---

### Post by whit on 2010-03-10
You say you can't seem to connect. But haven't described both sides of the connection that I can see. Or given the messages you see when a connection fails.

---

