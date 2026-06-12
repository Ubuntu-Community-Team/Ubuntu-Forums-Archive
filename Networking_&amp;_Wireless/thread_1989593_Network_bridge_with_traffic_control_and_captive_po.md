---
title: "Network bridge with traffic control and captive portal problems."
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by thebeest on 2012-05-28
Hi there

  I have been using Ubuntu since 6.04 and I cannot actually believe I have not posted on the forums until now!

I am setting up multiple networks on a site that each have different requirements. To best express the network layout I have drawn it up in a pretty diagram:

[IMG]http://i47.tinypic.com/2echnhc.jpg[/IMG]

So...

[LIST]
[*]The Home network already exists. All management off the Office and Camping networks takes place from the home network.
[*]The Camping network needs 2 wireless access points (configured presumably with OpenWrt) with a WifiDog server on the Linux box to provide a captive portal.
The site has a very poor broadband connection so for the home and office network to function correctly it is been deemed necessary to throttle the connection of the camping network, this will be done using tc on the linux box.
[*]The office network just needs internet access.
[/LIST]
Each network is kept isolated from the others. With the exception of management from the home network.

I have installed Ubuntu Server 12.04 on the Server. I have setup a bridge between the 2 ethernet cards eth1 and eth2 (eth0 is faulty and not used) in /etc/networking/interfaces. Routing works fine, I can connect to the Tenda Router attached to the server and brose the internet no trouble.

/etc/networking/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Device List 
auto eth1
auto eth2
auto br0

# The primary network interface
iface eth1 inet dhcp
address 192.168.0.100
netmast 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0

# Secondary network interface
#iface eth2 inet static
#address 192.168.1.100
#netmask 255.255.255.0
#gateway 192.168.0.1
#network 192.168.1.0
iface eth2 inet manual

iface br0 inet static
  bridge_ports eth2 eth1
  address 192.168.0.101
  netmask 255.255.255.0
  gateway 192.168.0.1
```

I started to play with tc, so far I am able to throttle the connection from the camping router with a bash script. But it will not let me throttle the connection for individual devices connected to the camping router. Presumably with OpenWRT on the routers I could set this up but it would make expanding the network more awkward as each router would require additional setup.

I really want the server to handle all throttling, logging and authentication with minimal setup on the routers. The working code I have so far is as follows:

config.sh
```
#!/bin/bash

mac[0]="AA:BB:CC:DD:EE:FF" #My Laptop
mac[1]="A1:B1:C1:D1:E1:F1" #My Android
```

bandwidth_shaping.sh
```
#!/bin/bash
#
#  All Rates are in Kbits, so in order to gets Bytes divide by 8
#  e.g. 25Kbps == 3.125KB/s
#

source "~/config.sh"
TC=/sbin/tc
EBTABLES=/sbin/ebtables   # Location of ebtables


IFIN=br0
IFOUT=eth2
 
tc_start() {
    $TC qdisc add dev $IFIN root handle 1:0 cbq bandwidth 100Mbit avpkt 1000 mpu 64
    $TC qdisc add dev $IFOUT root handle 1:0 cbq bandwidth 100Mbit avpkt 1000 mpu 64

#Limit all other connections
#768kbps download speed
${TC} class add dev $IFIN parent 1:0 classid 1:1 cbq rate 768KBit allot 1514 prio 1 avpkt 1000 bounded
${TC} filter add dev $IFIN parent 1:0 protocol ip handle 1 fw flowid 1:1
${EBTABLES} -A FORWARD -j mark --set-mark 1 --mark-target ACCEPT
#256kbps upload speed
${TC} class add dev $IFOUT parent 1:0 classid 1:1 cbq rate 256KBit allot 1514 prio 1 avpkt 1000 bounded
${TC} filter add dev $IFOUT parent 1:0 protocol ip handle 1 fw flowid 1:1
${EBTABLES} -A FORWARD -j mark --set-mark 1 --mark-target ACCEPT

#Do not rate shape MACs in config.sh
for element in $(seq 0 $((${#mac[@]} - 1)))
  do
  ${EBTABLES} -A FORWARD -s ${mac[$element]} -j ACCEPT
  ${EBTABLES} -A FORWARD -d ${mac[$element]} -j ACCEPT
done

}
 
tc_stop() {
    ${EBTABLES} -F
    $TC qdisc del dev $IFIN root
    $TC qdisc del dev $IFOUT root
}
 
tc_restart() {
    tc_stop
    sleep 1
    tc_start
}
 
tc_show() {
    echo ""
    echo "$IFIN"
    $TC qdisc show dev $IFIN
    $TC class show dev $IFIN
    $TC filter show dev $IFIN
    echo ""
    echo "$IFOUT"
    $TC qdisc show dev $IFOUT
    $TC class show dev $IFOUT
}
 
tc_stop() {
    ${EBTABLES} -F
    $TC qdisc del dev $IFIN root
    $TC qdisc del dev $IFOUT root
}
 
tc_restart() {
    tc_stop
    sleep 1
    tc_start
}
 
tc_show() {
    echo ""
    echo "$IFIN"
    $TC qdisc show dev $IFIN
    $TC class show dev $IFIN
    $TC filter show dev $IFIN
    echo ""
    echo "$IFOUT"
    $TC qdisc show dev $IFOUT
    $TC class show dev $IFOUT
    $TC filter show dev $IFOUT
}
case "$1" in
 
  start)
 
    echo -n "Starting bandwidth shaping: "
    tc_start
    echo "done"
    ;;
 
  stop)
 
    echo -n "Stopping bandwidth shaping: "
    tc_stop
    echo "done"
    ;;
 
  restart)
 
    echo -n "Restarting bandwidth shaping: "
    tc_restart
    echo "done"
    ;;
 
  show)
 
    tc_show
    ;;
 
  *)
 
    echo "Usage: bandwidth_shaping {start|stop|restart|show}"
    ;;
 
esac
```

So I need to work out how to throttle just the camping network and not the office network although it needs to pass through one of the camping routers. Also is it possible to bypass the throttling/authentication for a specified list of MACs? So an office/home device can pick up the camping network without going through the captive portal and being throttled.

The site is in a rural area and consequently extra cabling would involve digging trenches and is not really possible. I do have a redundant Ethernet cable running from the home network to near where the office network will be but ideally I want to use the layout specified in the diagram as the cabling is all underground and better shielded.

If anyone has any ideas or suggestions it would be greatly appreciated!

Cheers
  Mat

---

