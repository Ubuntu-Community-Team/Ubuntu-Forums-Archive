---
title: "Iptables + wireless access point + software router"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by KittyKitty on 2009-12-19
I have a laptop, it has a wired nic (eth1), a wireless nic (eth0), and dialup (ppp0).

The Wired nic is connected to my wireless access point. it is a linksys wrt54gls running tomatoe, it is setup as just an access point with nothing fancy smancy going on. my own nic and other wireless computer can access webpages on laptop's apache2 shares.

i am trying to setup iptables using firestarter,kmyfirewall or anyother iptables frontend to no avail. I am posting the script created by kmyfirewall

```
#!/bin/sh
#
# copyright (c) the KMyFirewall developers 2001-2007
# Please report bugs to: Christian Hubinger <chubinegr@irrsinnig.org>
#
# This program is distributed under the terms of the GPL v2
#
# KMyFirewall v1.1.1
# This is an automatic generated file DO NOT EDIT
#
# Configuration created for My Local Computer [127.0.0.1]
#

startFirewall() {

echo -n "Starting iptables (created by KMyFirewall)...       "
if [ "$verbose" = "1" ]; then
echo -n "
Loading needed modules...          "
fi


$MOD ip_tables 
$MOD ip_conntrack 
$MOD ipt_LOG 
$MOD ipt_limit 
$MOD ipt_state 
$MOD ip_conntrack_ftp
$MOD ip_conntrack_irc

$MOD iptable_filter
$MOD iptable_nat
$MOD iptable_mangle
if [ "$verbose" = "1" ]; then
echo "Done."
fi



#  Define all custom chains
if [ "$verbose" = "1" ]; then
echo -n "Create custom chains...       "
fi





if [ "$verbose" = "1" ]; then
echo "  Done."
fi



#  Rules:
if [ "$verbose" = "1" ]; then
echo "Settup Rules in Table FILTER:"
fi




#  Define Rules for Chain: INPUT
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: INPUT"
fi

                    
$IPT -t filter -A INPUT --match limit --limit 5/second --limit-burst 5 -p icmp --icmp-type echo-request -j ACCEPT  || { status="1"; echo " Setting up Rule: ICMP FAILED! Clearing Rules!";  stopFirewall; exit 1; }

$IPT -t filter -A INPUT --in-interface lo --source 127.0.0.1 -j ACCEPT  || { status="1"; echo " Setting up Rule: LOCALHOST FAILED! Clearing Rules!";  stopFirewall; exit 1; }

$IPT -t filter -A INPUT --match state --state RELATED,ESTABLISHED -j ACCEPT  || { status="1"; echo " Setting up Rule: CONNTRACK FAILED! Clearing Rules!";  stopFirewall; exit 1; }

$IPT -t filter -A INPUT -m limit --limit 5/second --limit-burst 5 -j LOG --log-prefix "KMF:" || { status="1"; echo " Setting up Rule: Chain: INPUT Drop Logging FAILED! Clearing Rules!";  stopFirewall; exit 1; }

$IPT -t filter -P INPUT DROP || { status="1"; echo " Setting up Rule: Chain: INPUT Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: OUTPUT
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: OUTPUT"
fi

                    
$IPT -t filter -P OUTPUT ACCEPT || { status="1"; echo " Setting up Rule: Chain: OUTPUT Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: FORWARD
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: FORWARD"
fi

                    
$IPT -t filter -P FORWARD ACCEPT || { status="1"; echo " Setting up Rule: Chain: FORWARD Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


if [ "$verbose" = "1" ]; then
echo "Settup Rules in Table NAT:"
fi




#  Define Rules for Chain: OUTPUT
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: OUTPUT"
fi

                    
$IPT -t nat -P OUTPUT ACCEPT || { status="1"; echo " Setting up Rule: Chain: OUTPUT Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: PREROUTING
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: PREROUTING"
fi

                    
$IPT -t nat -P PREROUTING ACCEPT || { status="1"; echo " Setting up Rule: Chain: PREROUTING Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: POSTROUTING
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: POSTROUTING"
fi

                    
$IPT -t nat -A POSTROUTING -j MASQUERADE  || { status="1"; echo " Setting up Rule: NAT_RULE FAILED! Clearing Rules!";  stopFirewall; exit 1; }

$IPT -t nat -P POSTROUTING ACCEPT || { status="1"; echo " Setting up Rule: Chain: POSTROUTING Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


if [ "$verbose" = "1" ]; then
echo "Settup Rules in Table MANGLE:"
fi




#  Define Rules for Chain: INPUT
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: INPUT"
fi

                    
$IPT -t mangle -P INPUT ACCEPT || { status="1"; echo " Setting up Rule: Chain: INPUT Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: OUTPUT
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: OUTPUT"
fi

                    
$IPT -t mangle -P OUTPUT ACCEPT || { status="1"; echo " Setting up Rule: Chain: OUTPUT Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: FORWARD
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: FORWARD"
fi

                    
$IPT -t mangle -P FORWARD ACCEPT || { status="1"; echo " Setting up Rule: Chain: FORWARD Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: PREROUTING
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: PREROUTING"
fi

                    
$IPT -t mangle -P PREROUTING ACCEPT || { status="1"; echo " Setting up Rule: Chain: PREROUTING Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


#  Define Rules for Chain: POSTROUTING
if [ "$verbose" = "1" ]; then
echo "Create Rules for Chain: POSTROUTING"
fi

                    
$IPT -t mangle -P POSTROUTING ACCEPT || { status="1"; echo " Setting up Rule: Chain: POSTROUTING Default Target FAILED! Clearing Rules!";  stopFirewall; exit 1; }


if [ "$verbose" = "1" ]; then
echo -n "Enable IP Forwarding.                "
fi



echo 1 > /proc/sys/net/ipv4/ip_forward
if [ "$verbose" = "1" ]; then
echo "Done."
fi


if [ "$verbose" = "1" ]; then
echo -n "Disable Reverse Path Filtering       "
fi


for i in /proc/sys/net/ipv4/conf/*/rp_filter ; do
echo 0 > $i 
done
if [ "$verbose" = "1" ]; then
echo "Done."
fi


if [ "$verbose" = "1" ]; then
echo -n "Disable log_martians (logging).           "
fi


for i in /proc/sys/net/ipv4/conf/*/log_martians ; do
echo 0 > $i 
done
if [ "$verbose" = "1" ]; then
echo "Done."
fi


if [ "$verbose" = "1" ]; then
echo -n "Enable Syn Cookies.          "
fi



echo 1 > /proc/sys/net/ipv4/tcp_syncookies
if [ "$verbose" = "1" ]; then
echo "Done."
fi


echo Done.
}
stopFirewall() {
  echo -n "Clearing iptables (created by KMyFirewall)...       "

  $IPT -t filter -F || status="1"
  $IPT -t filter -X || status="1"
  $IPT -t filter -P INPUT ACCEPT || status="1"
  $IPT -t filter -P OUTPUT ACCEPT || status="1"
  $IPT -t filter -P FORWARD ACCEPT || status="1"

  $IPT -t nat -F || status="1"
  $IPT -t nat -X || status="1"
  $IPT -t nat -P OUTPUT ACCEPT || status="1"
  $IPT -t nat -P PREROUTING ACCEPT || status="1"
  $IPT -t nat -P POSTROUTING ACCEPT || status="1"

  $IPT -t mangle -F || status="1"
  $IPT -t mangle -X || status="1"
  $IPT -t mangle -P INPUT ACCEPT || status="1"
  $IPT -t mangle -P OUTPUT ACCEPT || status="1"
  $IPT -t mangle -P OUTPUT ACCEPT || status="1"
  $IPT -t mangle -P PREROUTING ACCEPT || status="1"
  $IPT -t mangle -P POSTROUTING ACCEPT || status="1"

  echo "Done."

}
IPT="/sbin/iptables"
MOD="/sbin/modprobe"
status="0"
verbose="0"
action="$1"
if [ "$1" = "-v" ]; then
    verbose="1"
fi

if [ "$1" = "--verbose" ]; then
    verbose="1"
fi

if [ "$verbose" = "1" ]; then
    if [ "$2" = "" ]; then
    echo "Usage: sh kmyfirewall.sh [-v|--verbose] { start | stop | restart }"
    exit 1
  fi
action="$2"
fi

case $action in
  start)
  stopFirewall
  startFirewall
  ;;
  stop)
  stopFirewall
  ;;
  restart)
  stopFirewall
  startFirewall
  ;;
  *)
  echo "Invalid action!
Usage: sh kmyfirewall.sh [-v|--verbose] { start | stop | restart }"
  ;;
  esac

if [ "$status" = "1" ]; then
  exit 1
else
  exit 0
fi


```

enabling this 1/2 of the time leads to even the local machine not being able to use the internet untill i re-add the dialup adapter's default gateway into the routing table. another 1/4 of the time it just completely disables networking altogether requiring me to reboot my machine (errors when trying to use ping to the effect of operation not allowed) and last the other 1/4 of the time, the local host works fine, some remote hosts will work but can not use internet as nothing resolves because the iptables rules begin blocking all dnsmasq traffic

here is a snippet of dmesg | tail all the KMF crap is from the filtering script

```
[65045.673761] KMF:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:04:23:64:46:02:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308
[65045.678994] KMF:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:04:23:64:46:02:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308
[27849.623580] KMF:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:04:23:64:46:02:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308
[27849.630493] KMF:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:04:23:64:46:02:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308
[65092.741697] KMF:IN=eth0 OUT= MAC=00:04:23:64:46:02:00:1c:be:56:f7:08:08:00 SRC=192.168.0.117 DST=192.168.0.1 LEN=59 TOS=0x00 PREC=0x00 TTL=128 ID=15104 PROTO=UDP SPT=50869 DPT=53 LEN=39
[65098.323153] KMF:IN=eth0 OUT= MAC=00:04:23:64:46:02:00:1c:be:56:f7:08:08:00 SRC=192.168.0.117 DST=192.168.0.1 LEN=59 TOS=0x00 PREC=0x00 TTL=128 ID=15360 PROTO=UDP SPT=50869 DPT=53 LEN=39
[65277.285633] KMF:IN=eth1 OUT= MAC=00:00:00:60:06:e5:00:1e:e5:6c:9b:37:08:00 SRC=192.168.0.10 DST=192.168.0.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2057 DPT=514 LEN=49
[65277.292040] KMF:IN=eth1 OUT= MAC=00:00:00:60:06:e5:00:1e:e5:6c:9b:37:08:00 SRC=192.168.0.10 DST=192.168.0.1 LEN=93 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2057 DPT=514 LEN=73
[65277.293886] KMF:IN=eth1 OUT= MAC=00:00:00:60:06:e5:00:1e:e5:6c:9b:37:08:00 SRC=192.168.0.10 DST=192.168.0.1 LEN=81 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2057 DPT=514 LEN=61
[65277.541819] KMF:IN=eth1 OUT= MAC=00:00:00:60:06:e5:00:1e:e5:6c:9b:37:08:00 SRC=192.168.0.10 DST=192.168.0.1 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2057 DPT=514 LEN=66
[27949.189007] KMF:IN=eth1 OUT= MAC=00:00:00:60:06:e5:00:1e:e5:6c:9b:37:08:00 SRC=192.168.0.10 DST=192.168.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=47538 DF PROTO=TCP SPT=2169 DPT=445 WINDOW=5840 RES=0x00 SYN URGP=0
[65363.836986] KMF:IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=192.168.0.67 DST=192.168.0.67 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=68 DPT=67 LEN=308
```

if this doesn't affect the remote hosts, it sure affects the local one as all this information is piling up at Mb/min in my /var/log folder
and my laptop is running from a 4Gb microsd card.

any help would be greatly appriciated

---

### Post by shredder12 on 2009-12-20
I use firestarter and dhcp3 server to enable LAN internet sharing using my laptop..
But I am unable to understand what are you trying to do here?

In my case, I was getting internet connectivity thru wireless and I was using wired connection as the LAN. I guess you are trying to do something similar with the mediums switched.

Am I correct?

---

### Post by KittyKitty on 2009-12-25
My network setup is 
lo
eth1 <-> Wireless Access point (this is where i am trying to share the network to)
eth0 <-> Wireless card (not in use for this config)
ppp0 <-> Alltel dialup networking (internet connection to share)

the problem is that the firewall is blocking most any activity
the access point is a linksys wrt64gls running tomato, so i can ssh into it and issue commands like ping or even get webpages with wget but kmyfirewall is blocking
all the activity
the access point is static ip'd as 192.168.0.10
eth1 is static 192.168.0.1 (and runs the dhcp/dns server properly configured)
i had been running this same setup before with my wireless (eth0) as the gateway
but since i tried to switch the interfaces to ppp0 it has sense failed to operate properly.

no clue as to why, i'm trying to add more trusted zones to make it shut up, but havn't been able to test lately

---

### Post by shredder12 on 2009-12-25
have  you tried allowing connections from the firewall?

---

### Post by KittyKitty on 2009-12-26
With my limited knowledge of kmyfirewall, I am really lucky i can load the program
you say you run firestarter, screw it i'll load that up and see what it says.
cause i'm completely fed up with b.s. and if this is gonna be easier for you its easier for me

---

### Post by shredder12 on 2009-12-26
these help pages might be useful..
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

