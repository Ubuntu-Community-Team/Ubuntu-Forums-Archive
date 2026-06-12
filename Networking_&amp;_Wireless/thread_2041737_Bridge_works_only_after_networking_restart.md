---
title: "Bridge works only after networking restart"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by faugusztin on 2012-08-13
Hi,

i have set up my server (Ubuntu 12.04) , and tasked it among others with routing tasks as well. But i have a small issue, which i can workaround, but i would like to a correct solution.

Networking part :
1) eth0 - Intel 82574L NIC. It is connected to the internet, it gets it's public IPv4 address from the cable modem.
2) eth1 - Intel 82574L NIC. It is connected to the only "wired" computer on the network.
3) wlan0 - TP-LINK TL-WN881ND 802.11n card - it has an Atheros AR9287 on it, so it is handled by ath9k. This is used for wireless computers, using WPA/WPA2-PSK via hostapd.
4) eth1 and wlan0 are bridged via bridge_utils to br0.

Now the issue :
1) when i start up the computer, it brings up all interfaces, eth0 gets the correct DHCP assigned IP address from the cable modem, br0 gets it's correct static IP. But it seems that DHCP for local network doesn't work, at least not for the wireless part. Services like local DNS server, SSH, SMB etc are unreachable - in configuration files they are limited only to the local network interface, that means they either got br0 or 192.168.1.11 mentoined in their respective binding configuration directives.
2) after i restart the network using /etc/init.d/networking restart, then i restart isc-dhcp-server, bind9, ssh, smbd and the remaining services, all works without any issues. This is the workaround, but i don't like starting up the console after every reboot and restarting the whole networking stack and services.

Relevant parts of dmesg :
```
[    1.224334] e1000e: Intel(R) PRO/1000 Network Driver - 1.9.5-k
[    1.224336] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.224346] e1000e 0000:06:00.0: Disabling ASPM L0s L1
[    1.224522] e1000e 0000:06:00.0: (unregistered net_device): Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.224625] e1000e 0000:06:00.0: irq 59 for MSI/MSI-X
[    1.224633] e1000e 0000:06:00.0: irq 60 for MSI/MSI-X
[    1.224640] e1000e 0000:06:00.0: irq 61 for MSI/MSI-X
...
[    1.335708] e1000e 0000:06:00.0: eth0: (PCI Express:2.5GT/s:Width x1) 54:04:a6:b9:b6:dd
[    1.335710] e1000e 0000:06:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.335786] e1000e 0000:06:00.0: eth0: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    1.335797] e1000e 0000:07:00.0: Disabling ASPM L0s L1
[    1.336016] e1000e 0000:07:00.0: (unregistered net_device): Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.336125] e1000e 0000:07:00.0: irq 62 for MSI/MSI-X
[    1.336130] e1000e 0000:07:00.0: irq 63 for MSI/MSI-X
[    1.336134] e1000e 0000:07:00.0: irq 64 for MSI/MSI-X
...
[    1.447659] e1000e 0000:07:00.0: eth1: (PCI Express:2.5GT/s:Width x1) 54:04:a6:b9:b8:e7
[    1.447661] e1000e 0000:07:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    1.447742] e1000e 0000:07:00.0: eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
...
[   15.401071] cfg80211: Calling CRDA to update world regulatory domain
[   16.127144] ath: EEPROM regdomain: 0x809c
[   16.127146] ath: EEPROM indicates we should expect a country code
[   16.127148] ath: doing EEPROM country->regdmn map search
[   16.127149] ath: country maps to regdmn code: 0x52
[   16.127151] ath: Country alpha2 being used: CN
[   16.127152] ath: Regpair used: 0x52
[   16.127155] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.127157] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
... lots of wlan frequency stuff ...
[   16.523948] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.883637] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.883841] Registered led device: ath9k-phy0
[   16.883846] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc90007fa0000, irq=16
[   16.883949] cfg80211: Calling CRDA for country: CN
[   16.885963] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
... more frequency stuff ...
[   16.885999] cfg80211: Disabling freq 2484 MHz
[   16.886002] cfg80211: Regulatory domain changed to country: CN
[   16.886003] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.886004] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   16.886005] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   16.918650] ip_tables: (C) 2000-2006 Netfilter Core Team
...
[   17.179862] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.457142] Bridge firewalling registered
[   17.458240] device eth1 entered promiscuous mode
...
[   17.595413] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.597295] ADDRCONF(NETDEV_UP): br0: link is not ready
...
[   20.117861] ADDRCONF(NETDEV_UP): eth0: link is not ready
...
[   20.877555] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   20.878438] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   20.878462] br0: port 1(eth1) entered forwarding state
[   20.878465] br0: port 1(eth1) entered forwarding state
[   20.879139] ADDRCONF(NETDEV_CHANGE): br0: link becomes ready
...
[   23.173616] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   23.174493] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.364382] e1000e 0000:06:00.0: eth0: changing MTU from 1500 to 576
...
[   25.888733] e1000e 0000:06:00.0: eth0: Reset adapter
[   28.597653] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   28.598512] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.728623] br0: no IPv6 routers present
[   35.920656] br0: port 1(eth1) entered forwarding state
...
[   94.314367] device wlan0 entered promiscuous mode
[   94.315081] br0: port 2(wlan0) entered forwarding state
[   94.315085] br0: port 2(wlan0) entered forwarding state
...
[  109.329173] br0: port 2(wlan0) entered forwarding state
```

And this happens when i restart the network manually (/etc/init.d/networking restart) :

```
[  410.893101] br0: port 2(wlan0) entered disabled state
[  410.893133] br0: port 1(eth1) entered disabled state
[  410.980542] device eth1 left promiscuous mode
[  410.980548] br0: port 1(eth1) entered disabled state
[  411.005640] device wlan0 left promiscuous mode
[  411.005645] br0: port 2(wlan0) entered disabled state
[  411.121634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  413.942371] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  413.943987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  414.598617] device eth1 entered promiscuous mode
[  414.681118] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  414.682436] device wlan0 entered promiscuous mode
[  414.686217] br0: port 2(wlan0) entered forwarding state
[  414.686235] br0: port 2(wlan0) entered forwarding state
[  418.098462] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  418.100103] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  418.100139] br0: port 1(eth1) entered forwarding state
[  418.100155] br0: port 1(eth1) entered forwarding state
[  424.845535] br0: no IPv6 routers present
[  429.717643] br0: port 2(wlan0) entered forwarding state
[  433.109721] br0: port 1(eth1) entered forwarding state
```


Configuration files :

/etc/network/interfaces :
```
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp
auto eth1
auto wlan0

auto br0
iface br0 inet static
     address 192.168.1.11
     netmask 255.255.255.0
     gateway 192.168.1.11
     dns-nameservers 192.168.1.11
     dns-search local.auguszt.in
     bridge_ports eth1 wlan0
     pre-up iptables-restore < /etc/iptables.rules
```

/etc/hostapd/hostapd.conf :
```
interface=wlan0
bridge=br0
driver=nl80211
ssid=XXXXXXXX
channel=6
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=XXXXXXXX
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
```

/etc/iptables.rules :
```
*filter
:INPUT ACCEPT [1541:235811]
:FORWARD ACCEPT [26:8540]
:OUTPUT ACCEPT [1283:174942]
:MONITORIX_IN_0 - [0:0]
:MONITORIX_IN_1 - [0:0]
:MONITORIX_IN_2 - [0:0]
:MONITORIX_IN_3 - [0:0]
:MONITORIX_IN_4 - [0:0]
:MONITORIX_OUT_0 - [0:0]
:MONITORIX_OUT_1 - [0:0]
:MONITORIX_OUT_2 - [0:0]
:MONITORIX_OUT_3 - [0:0]
:MONITORIX_OUT_4 - [0:0]
-A FORWARD -i eth0 -o br0 -j ACCEPT
-A FORWARD -i br0 -o eth0 -j ACCEPT
COMMIT
*nat
:PREROUTING ACCEPT [57:3590]
:INPUT ACCEPT [13:797]
:OUTPUT ACCEPT [28:2181]
:POSTROUTING ACCEPT [5:820]
-A POSTROUTING -o eth0 -j MASQUERADE
COMMIT
```

Any ideas how to fix this ? FYI, i already modified the /etc/init files for required network services to start only after br0, but that doesn't help much as the issue is with br0 starting up without wlan0, which starts really slow (probably because hostapd starts after network started?) - i mean i changed :
```
start on runlevel [2345]
```
to :
```
start on (runlevel [2345] and net-device-up IFACE=br0)
```

---

### Post by faugusztin on 2012-08-14
Just a heads up - the issue was with :
1) the gateway line in the network configuration - main reason for my problems
2) wlan0 shouldn't be in the bridge, it will be automatically added to bridge by hostapd
3) the hostapd line is not needed :

So instead of :
```
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp
auto eth1
auto wlan0

auto br0
iface br0 inet static
     address 192.168.1.11
     netmask 255.255.255.0
     gateway 192.168.1.11
     dns-nameservers 192.168.1.11
     dns-search local.auguszt.in
     bridge_ports eth1 wlan0
     pre-up iptables-restore < /etc/iptables.rules
```

It should have been :
```
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

auto br0
iface br0 inet static
     address 192.168.1.11
     netmask 255.255.255.0
     dns-nameservers 192.168.1.11
     dns-search local.auguszt.in
     bridge_ports eth1
     post-up iptables-restore < /etc/iptables.rules
```

And the hostapd.conf needs a "bridge=br0" line.

---

### Post by darkwalt on 2012-08-19
Don't suppose you could post a tutorial on how to bridge connections in ubuntu or post a link to one?  Been trying to bridge laptop to x360 for a day now.

---

### Post by faugusztin on 2012-08-19
Well.

First you need bridge-utils :
```
apt-get install bridge-utils
```

Then you edit your network interfaces configuration (/etc/network/interfaces) :
```
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

auto br0
iface br0 inet static
     address 192.168.1.11
     netmask 255.255.255.0
     dns-nameservers 192.168.1.11
     dns-search local.auguszt.in
     bridge_ports eth1
     post-up iptables-restore < /etc/iptables.rules
```

In my case, eth0 is the connection to the internet, which gets all it's settings from providers DHCP server. If you need different configuration, then just change the iface eth0 inet dhcp line according to your needs.

The bridge magic is in the remaining lines:
[list]
[*]auto br0 - this says that br0 interface should be automatically started when you boot. 
[*]iface br0 inet static - says we configure this interface manually.
[*]address/netmask/dns-nameservers/dns-search - standard static IP & DNS configuration stuff. Change according to your needs.
[*]bridge_ports eth1 - this is where the fun starts. It says you want to include eth1 port in the bridge. This is because you cannot add uninitialized interfaces to the bridge now, that means wifi will be added later, not through this configuration. If you would have more wired ethernet interfaces, then you could enumerate them here - eth2 eth3 etc.
[*]post-up iptables-restore < /etc/iptables.rules - this sets the NAT iptables rules after we have the br0 interface up.[/list]

/etc/iptables.rules contains :
```
*filter
:INPUT ACCEPT [1541:235811]
:FORWARD ACCEPT [26:8540]
:OUTPUT ACCEPT [1283:174942]
-A FORWARD -i eth0 -o br0 -j ACCEPT
-A FORWARD -i br0 -o eth0 -j ACCEPT
COMMIT
*nat
:PREROUTING ACCEPT [57:3590]
:INPUT ACCEPT [13:797]
:OUTPUT ACCEPT [28:2181]
:POSTROUTING ACCEPT [5:820]
-A POSTROUTING -o eth0 -j MASQUERADE
COMMIT
```
These do the NAT. Don't ask me how they exactly work, i am not a iptables guru :D. But in short they allow the traffic pass from eth0 to br0 and back.

Now you wonder how will we get the WiFi in that bridge. That is the task for hostapd. Install it :
```
apt-get install hostapd
```
Edit the configuration file (/etc/hostapd/hostapd.conf) according to your needs. My configuration file looks like :
```
interface=wlan0
bridge=br0
driver=nl80211
ssid=YOURSSID
channel=6
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=YOURPASSPHRASE
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
```

[list][*]The interface=wlan0 defines what WiFi interface we want to configure, in my case it is wlan0.
[*]bridge=br0 - this will direct hostapd to add this interface to the br0 bridge after it finished configuring it.
[*]the remaining options configure the adapter to have specific SSID, operate as 802.11g as specific channel, set the encoding to WPA/WPA2 PSK and operate as 802.11n too (last two lines).[/list]

Set hostapd to start automatically, and probably restart the server to test out if all starts as it should. 

And that's all. Pretty simple huh ? It just took me few days to find the bits and pieces.

---

### Post by SeaKing on 2012-08-29
I'm in a similar fight with my bridge and your magic seems not to work for me ...
my config:

interface:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1

auto wlan0

auto br0
iface br0 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge-ports eth1
    post-up /usr/sbin/my_iptables_rules.sh

post-up /etc/init.d/isc-dhcp-server restart
post-up /etc/init.d/bind9 restart
```iptable rules:
```
# External (Internet-facing) interface
EXTIF="eth0"

# External IP address (automatically detected)
EXTIP=$(/sbin/ip addr show dev "$EXTIF" | perl -lne 'if(/inet (\S+)/){print$1;last}');
 
# Internal interface
INTIF="br0"

# Internal IP address (in CIDR notation)
INTIP="192.168.1.1/32"

# Internal network address (in CIDR notation)
INTNET="192.168.1.0/24"

# The address of anything/everything (in CIDR notation)
UNIVERSE="0.0.0.0/0"


echo "External: [Interface=$EXTIF] [IP=$EXTIP]"
echo "Internal: [Interface=$INTIF] [IP=$INTIP] [Network:$INTNET]"

echo
echo -n "Loading rules..."

# Enabling IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward


/sbin/iptables-restore <<-EOF;

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]

###################################################
# INPUT: Incoming traffic from various interfaces #
###################################################

# Loopback interface is valid
-A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interface, local machines, going anywhere is valid
-A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT


# Remote interface, claiming to be local machines, IP spoofing, get lost
-A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT


# External interface, from any source, for ICMP traffic is valid
-A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT


# Allow any related traffic coming back to the MASQ server in.
-A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT


# Internal interface, DHCP traffic accepted
-A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT

# Internal interface, DNS traffic accepted
-A INPUT -i $INTIF -p tcp --dport 53 -j ACCEPT
-A INPUT -i $INTIF -p udp --dport 53 -j ACCEPT

# External interface, HTTP/HTTPS traffic allowed
-A INPUT -i $EXTIF -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
-A INPUT -i $EXTIF -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 443 -j ACCEPT

# External interface, SSH traffic allowed
-A INPUT -i $EXTIF -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j ACCEPT

# Accept port 1234 to be forwarded (this rule needs to correspond with PREROUTING rules in NAT table)
-A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 1234 -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j ACCEPT

# Catch-all rule, reject anything else
-A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

#

####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################

# Workaround bug in netfilter
-A OUTPUT -m conntrack -p icmp --ctstate INVALID -j DROP

# Loopback interface is valid.
-A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interfaces, any source going to local net is valid
-A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
-A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


# outgoing to local net on remote interface, stuffed routing, deny
-A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT


# anything else outgoing on remote interface is valid
-A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


# Internal interface, DHCP traffic accepted
-A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
-A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT

# Internal interface, DNS traffic accepted
-A OUTPUT -o $INTIF -p tcp -s $INTIP --dport 53 -d 255.255.255.255 -j ACCEPT
-A OUTPUT -o $INTIF -p udp -s $INTIP --dport 53 -d 255.255.255.255 -j ACCEPT


# Catch all rule, all other outgoing is denied and logged. 
-A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

# Accept solicited tcp packets
-A FORWARD -i $EXTIF -o $INTIF -m conntrack --ctstate ESTABLISHED,RELATED  -j ACCEPT

# Allow packets across the internal interface
-A FORWARD -i $INTIF -o $INTIF -j ACCEPT

# Forward packets from the internal network to the Internet
-A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch-all REJECT rule
-A FORWARD -j REJECT

COMMIT


###########################
# Address translations (only; there is no actual forwarding done here)
###########################
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#-A PREROUTING -p tcp -d $EXTIP --dport 1234 -m conntrack --ctstate 

# ----- End OPTIONAL FORWARD Section -----

# IP-Masquerade
-A POSTROUTING -o $EXTIF -j MASQUERADE

COMMIT
EOF

echo " done."
```and hostapd.conf:
```
root@voyage:/usr/sbin# cat /etc/hostapd/hostapd.wlan0.conf 
interface=wlan0
driver=nl80211
logger_syslog=1
logger_syslog_level=2
logger_stdout=1
logger_stdout_level=2
debug=4
bridge=br0
#dump_file=/tmp/hostapd.dump
#ctrl_interface=/var/run/hostapd
#ctrl_interface_group=0
channel=6
hw_mode=g
macaddr_acl=0
auth_algs=3
eapol_key_index_workaround=0
eap_server=0
wpa=3
ssid=blablabla
wpa_passphrase=blablabla
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
eapol_version=1
#wme_enabled=1
ieee80211n=1
#ht_capab=[HT40-][HT40+][SHORT-GI-40][TX-STBC][RX-STBC1][DSSS_CCK-40]

```and (re)starting the network brings up:
```

Ignoring unknown interface eth1=eth1.
Ignoring unknown interface wlan0=wlan0.
[  484.638254] device eth1 entered promiscuous mode
[  484.675612] ADDRCONF(NETDEV_UP): br0: link is not ready

Waiting for br0 to get ready (MAXWAIT is 30 seconds).
External: [Interface=eth0] [IP=192.168.0.15/24]
Internal: [Interface=br0] [IP=192.168.1.1/32] [Network:192.168.1.0/24]

Loading rules... done.
Stopping ISC DHCP server: dhcpd failed!
Starting ISC DHCP server: dhcpdcheck syslog for diagnostics. ... failed!
 failed!
Failed to bring up br0.
done.


```eth0 is correctly initialized

---

### Post by kalosh on 2012-08-30
Hi.
In my case the "proper" config doesn't work. When I put bridge=br0 in hostapd.conf and in intefaces remove wlan0 from the bridge-ports, wlan0 device is not discovered by the system and wireless network is not broadcasting. Currently I have the problem, like you, faugusztin, had before. I have to restart networking and dhcp server to have internet broadcast to my devices. Does anyone has any idea according this problem?
Best regards, Dawid.
```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 195.66.145.26
        netmask 255.255.255.248
        gateway 195.66.145.25
        pre-up iptables-restore < /usr/etc/iptables.config

auto wlan0
iface wlan0 inet manual

auto br0
iface br0 inet static
address 10.10.10.1
netmask 255.255.255.0
network 10.10.10.0
bridge-ports eth0 wlan0

``````
cat /etc/hostapd/hostapd.conf
ctrl_interface=/var/run/hostapd
###############################
# Basic Config
###############################
macaddr_acl=0
auth_algs=1
# Most modern wireless drivers in the kernel need driver=nl80211
driver=nl80211
##########################
# Local configuration...
##########################
interface=wlan0
#bridge=br0
hw_mode=g
channel=6
ssid=asdfasdf
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=asdfasdfasdf
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
dump_file=/var/log/hostapd.dump

``````

ifconfig
br0       Link encap:Ethernet  HWaddr 00:c0:a8:e4:ae:84
          inet addr:10.10.10.1  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fee4:ae84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:429667 (429.6 KB)  TX bytes:1240896 (1.2 MB)

eth0      Link encap:Ethernet  HWaddr 70:71:bc:d5:99:25
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:440337 (440.3 KB)  TX bytes:1557150 (1.5 MB)
          Interrupt:44

eth1      Link encap:Ethernet  HWaddr 00:08:a1:47:e3:fd
          inet addr:195.66.145.26  Bcast:195.66.145.31  Mask:255.255.255.248
          inet6 addr: fe80::208:a1ff:fe47:e3fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2095737 (2.0 MB)  TX bytes:1764655 (1.7 MB)
          Interrupt:20 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:149228 (149.2 KB)  TX bytes:149228 (149.2 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 00-C0-A8-E4-AE-84-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28794 (28.7 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:e4:ae:84
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:331958 (331.9 KB)  TX bytes:648377 (648.3 KB)


```
faugusztin, could you please answer me to following questions:
1. In the first (wrong) configuration wlan0 was visible in the ifconfig?
2. What interfaces do you have in correct config under ifconfig?
Any help would be appreciated.

---

### Post by faugusztin on 2012-08-30
> **kalosh said:**
> faugusztin, could you please answer me to following questions:
1. In the first (wrong) configuration wlan0 was visible in the ifconfig?
2. What interfaces do you have in correct config under ifconfig?
Any help would be appreciated.

1. wlan0 was visible every time. In my case the issue was not with wlan0 not starting, but with the whole thing starting slow. As you can see, ath9k driver starts setting up the driver 16 seconds after the boot compared to one second and something for the wired ethernet. And after that, it takes about a minute for the interface to reach the "ready" state.
2. eth0 (configured, DHCP), eth1 (not configured), lo (configured, 127.0.0.1), mon.wlan0 (not configured), wlan0 (not configured), br0 (configured, static IP).

Just to be clear, i did the following :
1) configured my eth0 with a DHCP client because it is my internet connectivity (see in my previous post)
2) configured my eth1 to be part of autostarting br0 bridge with static IP configuration (see in my previous post). I didn't add the wlan0 interface because of point 3 bellow.
3) set the Wireless configuration in hostapd.conf and configured that it should add the wlan interface automatically to the br0 bridge after the hostapd is ready with the interface. Reason :
[https://bugs.gentoo.org/show_bug.cgi?id=298824](https://bugs.gentoo.org/show_bug.cgi?id=298824)
> The problem is, that from now on, it is no longer possible to add a wireless interface that hasen't been configured to a bridge (which is what that patch does).

Upstream says, that the correct way to do it, is in exclude the wireless interface from the bridge, use >=hostapd-0.7.1, and let hostapd add the wireless interface to the bridge after it has configured it.
4) i think i had hostapd autostarting (update-rc.d hostapd defaults). That way once the wlan0 shows up, hostapd takes it into care, configures it and then automatically adds it to the bridge.

The question is, what driver are you using ?
> # [b]In case of madwifi, atheros, and nl80211 driver interfaces, an additional
# configuration parameter, bridge, may be used to notify hostapd if the
# interface is included in a bridge. This parameter is not used with Host AP
# driver. [/b] If the bridge parameter is not set, the drivers will automatically
# figure out the bridge interface (assuming sysfs is enabled and mounted to
# /sys) and this parameter may not be needed.
#
# For nl80211, this parameter can be used to request the AP interface to be
# added to the bridge automatically (brctl may refuse to do this before hostapd
# has been started to change the interface mode). If needed, the bridge
# interface is also created.

@SeaKing: did you tried with the minimal configuration i provided ? You got an awfull more stuff in your scripts and anything from that can fail. Why do you have the post-up stuff or "auto wlan0" and "auto eth1" lines ? Why so much iptables rules during the testing ? I know it sounds harsh from me, but shouldn't you get rid of all of the stuff which can fail, and start from a minimal example and if it works, add the rest you require ?

And to both of you - a bridge with single ethernet port and iptables with NAT masquerade should work any time. If you having issues making it work without the wlan interface, then you screwed up something else even before wireless comes into play. Try to make the non-wireless part of the whole bridge/NAT thing working, and once you have that, try to start up hostapd. You should then see wlan0 in output of "brctl show" and it should just work, because hostapd will add your wireless interface to the bridge by itself.

PS: There are some wifi drivers which needs something called ebtables, but don't ask me about that, i didn't need to use that one.

---

### Post by SeaKing on 2012-09-02
Well I found my mistake:

The config file is called hostapd.**wlan0**.conf (what I edited)
but in /etc/default/hostapd I posted in /etc/hostapd/hostapd.conf instead of /etc/hostapd/hostapd.**wlan0**.conf now it works fine.

BTW: it doesn't matter if you take "bridge-ports wlan0 eth1" or only "bridge-ports eth1". First one only brings you 1 error message more but makes no difference in the end

---

