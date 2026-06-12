---
title: "error while creating wireless network - set failed on device; network is down"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by lightsabersetc on 2010-01-16
Hey everyone, I have been working on this for a while now and am absolutely stumped. Basically, what i am attempting to do is make my ubuntu box into a gateway for my network. I have everything working thru hard wire, but I simply cant get the wireless to work. No matter what I do, I cannot get my wireless card to transmit an essid and allow nodes to connect. I have tried assigning it in the interfaces file (shown below), and I have also tried manually modifying it using the iwconfig command. Here is the topology:
eth1: internet WAN
eth2: ethernet out to LAN
ra0: wireless out to LAN

Here is a copy of my /etc/network/interfaces file:
```

auto lo
iface lo inet loopback
auto eth2
iface eth2 inet static
        address 192.168.0.102
        netmask 255.255.255.0
        broadcast 192.168.0.0
        network 192.168.0.0
auto eth1
iface eth1 inet dhcp

auto ra0
iface ra0 inet static
	address 192.168.2.102
	netmask 255.255.255.0
	broadcast 192.168.2.0
	network 192.168.2.0
#wireless-mode Ad-Hoc
#wireless-essid laz
wpa-driver wext
wpa-ssid las
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 56a72e371fd87baef20cda1a198f2972e479890dbe982ed336de33293c20d891  [CODE]

route command:
[CODE]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 ra0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
98.160.136.0    *               255.255.252.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         ip98-160-136-1. 0.0.0.0         UG    100    0        0 eth1
```

ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:1a:66:4b:51:b0  
          inet addr:98.160.137.113  Bcast:98.160.139.255  Mask:255.255.252.0
          inet6 addr: fe80::21a:66ff:fe4b:51b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:890686 errors:744 dropped:0 overruns:0 frame:744
          TX packets:614991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1068172509 (1.0 GB)  TX bytes:73325990 (73.3 MB)

eth2      Link encap:Ethernet  HWaddr 00:25:11:73:89:75  
          inet addr:192.168.0.102  Bcast:192.168.0.0  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56456 (56.4 KB)  TX bytes:56456 (56.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:1a:ef:07:4b:4a  
          inet addr:192.168.2.102  Bcast:192.168.2.0  Mask:255.255.255.0
          inet6 addr: fe80::21a:efff:fe07:4b4a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:599565 (599.5 KB)  TX bytes:0 (0.0 B)
          Interrupt:22 
```

ifdown -v ra0 && ifup -v ra0:
```

Configuring interface ra0=ra0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/clamav-freshclam-ifupdown
run-parts: executing /etc/network/if-down.d/openvpn
run-parts: executing /etc/network/if-down.d/upstart
run-parts: executing /etc/network/if-down.d/wpasupplicant

ifconfig ra0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/bridge
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.ra0.pid
Stopped /sbin/wpa_supplicant (pid 31784).
wpa_supplicant: removing /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplicant.ra0.pid
Configuring interface ra0=ra0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/bridge
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.ra0.pid -i ra0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplicant.ra0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/ra0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "las" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise TKIP CCMP -- OK
wpa_supplicant: wpa-group TKIP CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto WPA RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

ifconfig ra0 192.168.2.102 netmask 255.255.255.0 broadcast 192.168.2.0 	   	up

run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/clamav-freshclam-ifupdown
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/openvpn
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

Last, but not least-iwconfig:
```
lo        no wireless extensions.

eth2      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.437 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

```

During the ifup command, you can even see where the system "successfully" assigns the essid and psk to the device. Am i missing a step somewhere or is my syntax just incorrect? Any help would be greatly appreciated :)

---

### Post by tekknokrat on 2010-05-04
Old thread, did you solve your issue? 
I would recommend commenting all extra wpa- options out and then test.
```

wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
```

What is your Ubuntu Version?

---

### Post by lightsabersetc on 2010-05-04
Thank you for your reply. I am using ubuntu version 9.10. I ended up trying to get this to work for a little over a week and returned the wireless card for a wireless router lol. It turns out that the driver provided by Ralink will not work with master mode on kernels above v. 2.6. Upon researching further, I found that most wireless cards will not function at 300mbps wireless N in linux-especially in master mode. I wish I could have gotten it to work

---

