---
title: "A Simple script to Grab all important network info for diagnosing problems"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by oobe-feisty on 2009-05-12
here i wrote a script for people who need help with there network problems the idea is that is grabs all info about your networking configuration and hardware then outputs to a text file called network.txt then you can put it in pastebin in help channels or paste it here in this forum. the script will be supported and updated from this page on my new site [http://insidiousramblings.com/blog/?p=16](http://insidiousramblings.com/blog/?p=16)
 
you can dload it from here 

[http://insidiousramblings.com/files/netest.sh](http://insidiousramblings.com/files/netest.sh)

usage example 

wget [http://insidiousramblings.com/files/netest.sh](http://insidiousramblings.com/files/netest.sh)

chmod a+x netesh.sh 

./netest.sh

the copy and paste contents into pastebin or thread

here is an example of what the output file looks like

```
************ netstat -i *************
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0   8579749      0      0 0       8032798      0      0      0 BMRU
lo        16436 0   1453962      0      0 0       1453962      0      0      0 LRU
wlan0      1500 0    255537      0      0 0        479320      0      0      0 BMRU
wmaster0      0 0         0      0      0 0             0      0      0      0 RU
************ netstat -rn ( same as route -n ) *************
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
************ contents of /etc/resolv.conf  *************
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 203.12.160.35
nameserver 203.12.160.36
************ contents of /etc/hosts  *************
127.0.0.1	localhost
127.0.1.1	box
192.168.1.12    frontend
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
************ contents of /etc/network/interfaces  *************
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
up route add default gw 192.168.0.1


************ dig google.com  *************

; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 737
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		21	IN	A	209.85.171.100
google.com.		21	IN	A	74.125.67.100
google.com.		21	IN	A	74.125.45.100

;; Query time: 318 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Wed May 13 04:17:45 2009
;; MSG SIZE  rcvd: 76

************ host google.com  *************
google.com has address 74.125.67.100
google.com has address 74.125.45.100
google.com has address 209.85.171.100
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
************ nslookup   *************
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.67.100
Name:	google.com
Address: 74.125.45.100
Name:	google.com
Address: 209.85.171.100

************ nslookup using opendns  *************
Server:		208.67.222.220
Address:	208.67.222.220#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.67.100
Name:	google.com
Address: 74.125.45.100
Name:	google.com
Address: 209.85.171.100

************ lshw -C network  *************
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:e5:f0:18:7e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.10 latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:b9:5c:d9:75:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
************ lspci -vvv | grep Ethernet *************
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
************ lspci -vvv | grep Net *************
01:06.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
************ lspci -vvv | grep Wireless *************
```

---

