---
title: "Network manager script for virtualbox bridging"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by delerious010 on 2009-02-18
I'm using Virtualbox in bridged mode so that the VM can pull addresses via DHCP. This is an a laptop that disconnects every so often as I switch to a conference room or that alternates between wired and wireless. 

Because of this, I've chosen to tie in the bridge creation into Networkmanager. And it works, for the most part.

The only real problem I've noticed so far, is that Networkmanager tries to pull a DHCP address over eth0 rather than over my bridge. My scripts include an ugly temporary workaround, but don't fix this issue. 

If someone could provide a proper solution, it would be appreciated !

Anyhow .. I based on the bridging configurations on the post at ( thanks! ) : [http://ubuntuforums.org/showthread.php?t=558971](http://ubuntuforums.org/showthread.php?t=558971)

Basically, it gives me the following environment : 
- tap0 :
[INDENT]* 10.254.0.2 / 255.255.255.252[/INDENT]
[INDENT]* bridged[/INDENT]
- eth0:0 :
[INDENT]* 10.254.0.1 / 255.255.255.252[/INDENT]
[INDENT]* bridged[/INDENT]
- eth0 :
[INDENT]* unset, kind of -- Networkmanager has a lease for it. I clear the [/INDENT]default route and zero out the ip.
- br0 : 
[INDENT]* dhcp[/INDENT]
[INDENT]* default route kept[/INDENT]

I made a few quick scripts so that it would work with wifi / lan. They work, so I'm posting them in case someone finds em useful.

/etc/network/custom/netlibs
```

#!/bin/bash
 
 match_if_bydev () {
     IF="$1"
 
     MATCH=$(ip addr show dev $IF &> /dev/null)
     return $?
 };
 
 match_if_byaddr () {
     IF="$1"
     IP_ADD="$2"
     IP_MSK="$3"
 
     MATCH=$(ip addr show dev $IF to ${IP_ADD}/${IP_MSK})
     if [ -n "$MATCH" ]
     then return 0
     else return 1
     fi
 };
 
 match_route () {
     IF="$1"
     IP_ADD="$2"
     IP_MSK="$3"
     EXACT=""
 
     [ -n "$4" ] && EXACT="exact"
 
     MATCH=$(ip route show dev $IF ${EXACT} ${IP_ADD}/${IP_MSK})
     if [ -n "$MATCH" ]
     then return 0
     else return 1
     fi
 };

```
 
/etc/network/custom/bridge-vbox
ln to /etc/network/if-up.d/bridge-vbox
ln to /etc/network/if-down.d/bridge-vbox

```

#!/bin/bash
 
 . /etc/network/custom/netlibs
 
 IF="$IFACE"
 STATUS="$PHASE"
 #IF="$1"
 #STATUS="$2"
 BR_NET="10.254.0"
 BR_MASK="255.255.255.252"
 
 if [ ! "$IF" == "wlan0" ] && [ ! "$IF" == "eth0" ]
 then exit 0
 fi
 
 if [ "$STATUS" == "down" ]
 then
 
     if $(match_if_bydev "br0") && \
        $(match_if_bydev "${IF}:0") && \
        $(match_if_bydev "tap0")
     then
 
         if $(match_route tap0 "${BR_NET}.1" 32 exact)
         then route del -host "${BR_NET}.1"
         fi
 
         ifconfig br0 down
         brctl delif br0 tap0
         brctl delif br0 ${IF}:0
         brctl delbr br0
 
         ifconfig tap0 down
         #tunctl -d tap0 -- device in use X_x .. doh.
 
         ifconfig ${IF}:0 down
     fi
 
 elif [ "$STATUS" == "up" ]
 then
 
     if ! $(match_if_bydev "tap0")
     then tunctl -t tap0 -u serafini
     fi
 
     if ! $(match_if_bydev "${IF}:0") || \
        ! $(match_if_byaddr "${IF}:0" "${BR_NET}.1" 24)
     then ifconfig ${IF}:0 ${BR_NET}.1 netmask ${BR_MASK} up
     fi
 
     if ! $(match_if_bydev "br0")
     then
         brctl addbr br0
         #ifconfig ${IF} down -- loops NetworkManager .. doh.
         ifconfig ${IF} 0.0.0.0 promisc up
         route del -net 0.0.0.0/0 dev ${IF}
         brctl addif br0 ${IF}:0
         dhclient br0 &> /dev/null
         brctl addif br0 tap0
         ifconfig tap0 ${BR_NET}.2 netmask ${BR_MASK} up
         bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
         route add -host ${BR_NET}.1 dev tap0
         arp -Ds ${BR_NET}.1 ${IF}:0 pub
     fi
 fi


```

---

