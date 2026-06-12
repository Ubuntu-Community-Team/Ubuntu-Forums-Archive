---
title: "Bridge Network issues"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by mytinytown on 2011-06-22
I have a server with eth0 (7 port LAN switch), eth1 WAN and wlan0 wireless pcmcia.
I have wlan0 in master mode to have it work as an access point. I have my router plugged in to eth1 WAN. I server has full network and internet access. But if I log in to the access point (wlan0) I get network, no internet access. I did an experiment this weekend and found if I plug my router in to the (eth0) LAN switch the server gets full network and internet access, the access point still the same. But if I plug the router in to the WAN as I said the server works 100% I get only network, no internet even in the LAN switch. I feel my issue id either IP forwarding or bridging. My server is acting up right now or I would give you the print out of ifconfig, iwconfig and my network/interface file.

Is there anything I could try or anything else needed to get any help with this issue?

Oh my IPtables are fine too. It does the same with and with out them running (I used the IPtables that Ubuntu gave on its bridge network page).

---

### Post by mytinytown on 2011-06-22
ifconfig
```

br0       Link encap:Ethernet  HWaddr 00:09:5b:3b:1f:d5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:c6ff:fe18:6de0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53161 (53.1 KB)  TX bytes:57312 (57.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:10:c6:18:6d:e0  
          inet6 addr: fe80::210:c6ff:fe18:6de0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26611 (26.6 KB)
          Interrupt:10 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:10:c6:18:7b:e4  
          inet6 addr: fe80::210:c6ff:fe18:7be4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57232 (57.2 KB)  TX bytes:57352 (57.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11012 (11.0 KB)  TX bytes:11012 (11.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-3B-1F-D5-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x100 

wlan0     Link encap:Ethernet  HWaddr 00:09:5b:3b:1f:d5  
          inet6 addr: fe80::209:5bff:fe3b:1fd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x100 
```


iwconfig
```

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

br0       no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"**********"  
          Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:restricted
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"**********"  
          Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0
```


interfaces
```
# The loopback network interface
	auto lo
	iface lo inet loopback
	address 127.0.0.1
	netmask 255.0.0.0


# Switch (LAN)
	auto eth0
	iface eth0 inet manual


# WAN
	auto eth1
	iface eth1 inet dhcp


# Wireless
	auto wlan0
	iface wlan0 inet manual 
	wireless-mode master
	wireless-key **********************
	wireless-channel 4
	wireless-essid **********


#Bridge the above
	auto br0
	iface br0 inet static
	bridge_ports eth0 eth1 wlan0
	address 192.168.2.2
	netmask 255.255.255.0
	network 192.168.1.0
	gateway 192.168.2.1
	broadcast 192.168.2.255

```

IPTables
```
echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe

EXTIF="eth0"
INTIF="eth1"

echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing == 
echo -en "   loading modules: "
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "----------------------------------------------------------------------"
echo -en "ip_tables, "
$MODPROBE ip_tables
echo -en "nf_conntrack, " 
$MODPROBE nf_conntrack
echo -en "nf_conntrack_ftp, " 
$MODPROBE nf_conntrack_ftp
echo -en "nf_conntrack_irc, " 
$MODPROBE nf_conntrack_irc
echo -en "iptable_nat, "
$MODPROBE iptable_nat
echo -en "nf_nat_ftp, "
$MODPROBE nf_nat_ftp
echo "----------------------------------------------------------------------"
echo -e "   Done loading modules.\n"
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr 
echo "   Clearing any existing rules and setting default policy.."

iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
COMMIT
EOF

echo -e "\nrc.firewall-iptables v$FWVER done.\n"
```

It worked the same with the firewall on and after I flushed the firewall.

If you need any more information, please let me know!
Thank you!

---

### Post by mytinytown on 2011-06-25
Nobody willing to give me any advice?

I did forget to add I am using Ubuntu 10.02 server.

I tried to remove the bridge connections and make them standard and I completely lost my network. So I will try any ideas anyone is willing to offer.

---

### Post by mytinytown on 2011-06-28
I went through and set it up like this and still no internet.

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

---

### Post by mytinytown on 2011-06-29
Killed it, I removed the bridge connection and lost internet from everything.

I will start a new thread on what I have now, after looking at a few others.

---

### Post by mytinytown on 2011-07-06
Reinstalled Bridge and everything worked

---

