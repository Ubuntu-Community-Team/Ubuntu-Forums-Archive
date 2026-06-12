---
title: "using workstation as wireless AP"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2011-01-07
Hello again. 

I am looking to set my laptop up as a wireless AP which will allow various clients to connect to the wireless nic (wlan0), then funnel traffic to the wired nic (eth0), then on to the router, modem and Internet. I followed [this guide]("https://help.ubuntu.com/community/Router") and while I've gotten about halfway to my desired results, I've run into a wall. 

I have made the changes to /etc/network/interfaces, and have successfully run the nat.sh script (or so I thought). Upon restarting my networking, the wireless AP is available, or at least appears to be. However, the laptop is unable to ping the router or Internet hosts via eth0, and when I connect to the AP, I pull a 169.x.x.x IP address, not the expected 192.168.1.xx address. 

My modified /etc/network/interfaces:
```

# Loopback Interface
auto lo
iface lo inet loopback

#Wired Interface
auto eth0
iface eth0 inet dhcp

# Set up the internal wireless network
#
# If you would like to use WEP, uncomment the line 'wireless-key'
# and replace '<key goes here>' with a WEP key.
# 
# You may also change the network essid and channel.
#
auto wlan0
iface wlan0 inet manual
    wireless-mode master
    wireless-essid "UbuntuAP"
    wireless-channel 6
    #wireless-key <key goes here>


# Set up the internal wired/wireless network bridge
#
# Don't forget to change wlan0 and eth1 to the proper name of
# the internal wired and wireless interfaces if applicable.
#
auto br0
iface br0 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    bridge-ports eth0 wlan0
```

And my ammended nat.sh
```
echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe

EXTIF="eth0"
INTIF="wlan0"
#INTIF2="eth0"
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

Please point me in the direction of other resources, better, or different approaches to this so I can better understand how to funnel the wireless traffic through this host.

---

### Post by PatchesTheCaveman on 2011-01-07
You can't use both the wireless bridge and NAT feature at the same time.  You must use one or the other.  The NAT option makes your computer act like a router and firewall the wireless connections from the rest of network.  The bridge option lets the wireless clients get their IP address and connection directly from the router.

---

### Post by sp0nge on 2011-01-08
Thanks for the input. Helpful and enlightening. 

I started the process over and simply made the change to /etc/network/interfaces, and restarted /etc/init.d/networking. After setting the interfaces, I had to create the wireless network:

Network Manager>Create New Wireless Network
Connection: new
Network Name: MyNetwork
Wireless Security: None
Key: Blank

Then click create. 

I was then able to scan for networks and locate "MyNetwork", and connect to the AP, all traffic appears to be funneling properly. I now have a machine in between my devices and my router. 

Thanks again for the nudge in the right direction. I'm sure I did this before I posted, but it worked now!

---

