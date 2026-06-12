---
title: "Kmyfirewall problems"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by thrawntap on 2006-02-27
Hello

When I run firewall I've made with Kmyfirewall, my connection stops


```
joe@ubuntu:/media/data/$ ifconfig
eth0      Lien encap:Ethernet  HWaddr 00:11:2F:A2:91:59
          adr inet6: fe80::211:2fff:fea2:9159/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:2281849 (2.1 MiB)  TX bytes:1033160 (1008.9 KiB)
          Interruption:17

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:4571 (4.4 KiB)  TX bytes:4571 (4.4 KiB)

ppp0      Lien encap:Protocole Point-à-Point
          inet adr:80.170.164.184  P-t-P:80.170.128.1  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:2891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3
          RX bytes:2200858 (2.0 MiB)  TX bytes:946372 (924.1 KiB)
```

```
#!/bin/sh
#
# copyright (c) the KMyFirewall developers 2002
#      mail to: Christian Hubinger <e9806056@student.tuwien.ac.at>
#
# KMyFirewall v0.9.6.2
# This is an automatic generated file DO NOT EDIT
#
IPT="/sbin/iptables"
MOD="/sbin/modprobe"
status="0"

startFirewall() {
echo
echo "Starting firewall..."
echo -n "Loading needed modules...          "
$MOD ip_tables 
$MOD ip_conntrack 
$MOD ipt_LOG 
$MOD ipt_limit 
$MOD ipt_state 
$MOD ip_conntrack_ftp
$MOD ip_conntrack_irc
$MOD iptable_filter
echo "Done."
#  Define all custom chains
echo -n "Create custom chains...                "
  echo "Done."

#  Rules:

echo "Settup Rules in Table FILTER:
"

#  Define Rules for Chain: INPUT
echo -n "Create Rules for Chain: INPUT                    "
$IPT -t filter -A INPUT --protocol icmp   --icmp-type echo-request --match limit --limit 5/minute -j ACCEPT  || { status="1"; echo "Setting up Rule: PING_INPUT FAILED !!!"; exit 1; }

$IPT -t filter -A INPUT --match state --state RELATED,ESTABLISHED -j ACCEPT  || { status="1"; echo "Setting up Rule: CONNRACK_INPUT FAILED !!!"; exit 1; }

$IPT -t filter -A INPUT --destination 127.0.0.1 --in-interface lo -j ACCEPT  || { status="1"; echo "Setting up Rule: LOOPBACK_INPUT FAILED !!!"; exit 1; }

$IPT -t filter -A INPUT -m limit --limit 1/second --limit-burst 5 -j LOG --log-prefix "KMF: " || { status="1"; echo "Setting up Rule: Chain: INPUT Drop Logging FAILED !!!"; exit 1; }

$IPT -t filter -P INPUT DROP || { status="1"; echo "Setting up Rule: Chain: INPUT Default Target FAILED !!!"; exit 1; }

echo "Done."

#  Define Rules for Chain: OUTPUT
echo -n "Create Rules for Chain: OUTPUT                    "
$IPT -t filter -A OUTPUT --protocol icmp  -j ACCEPT  || { status="1"; echo "Setting up Rule: PING_OUTPUT FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --source 127.0.0.1 --out-interface lo -j ACCEPT  || { status="1"; echo "Setting up Rule: LOOPBACK_OUTPUT FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol udp  --destination-port 53 -j ACCEPT  || { status="1"; echo "Setting up Rule: DNS_UDP FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 53 -j ACCEPT  || { status="1"; echo "Setting up Rule: DNS_TCP FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 80 -j ACCEPT  || { status="1"; echo "Setting up Rule: WWW FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 8080 -j ACCEPT  || { status="1"; echo "Setting up Rule: WWW-PROXY FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 443 -j ACCEPT  || { status="1"; echo "Setting up Rule: SEC_WWW FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 25 -j ACCEPT  || { status="1"; echo "Setting up Rule: SMTP FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 110 -j ACCEPT  || { status="1"; echo "Setting up Rule: POP3 FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 995 -j ACCEPT  || { status="1"; echo "Setting up Rule: SEC_POP3 FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 143 -j ACCEPT  || { status="1"; echo "Setting up Rule: IMAP FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 585 -j ACCEPT  || { status="1"; echo "Setting up Rule: SEC_IMAP FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --protocol tcp  --destination-port 21 -j ACCEPT  || { status="1"; echo "Setting up Rule: FTP FAILED !!!"; exit 1; }

$IPT -t filter -A OUTPUT --match state --state RELATED,ESTABLISHED -j ACCEPT  || { status="1"; echo "Setting up Rule: CONNRACK_OUTPUT FAILED !!!"; exit 1; }

$IPT -t filter -P OUTPUT DROP || { status="1"; echo "Setting up Rule: Chain: OUTPUT Default Target FAILED !!!"; exit 1; }

echo "Done."

#  Define Rules for Chain: FORWARD
echo -n "Create Rules for Chain: FORWARD                    "
$IPT -t filter -P FORWARD DROP || { status="1"; echo "Setting up Rule: Chain: FORWARD Default Target FAILED !!!"; exit 1; }

echo "Done."
echo -n "Disable IP Forwarding.        "
echo 0 > /proc/sys/net/ipv4/ip_forward
echo "Done.
"

 echo -n "Enable Reverse Path Filtering      "
for i in /proc/sys/net/ipv4/conf/*/rp_filter ; do
echo 2 > $i 
done
echo "Done."
echo -n "Disable log_martians (logging).           "
for i in /proc/sys/net/ipv4/conf/*/log_martians ; do
echo 0 > $i 
done
echo "Done.
"

 echo -n "Enable Syn Cookies.          "
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo "Done."
}
stopFirewall() {
  echo -n "Shutdown KMyFirewall...       "

  $IPT -t filter -F || status="1"
  $IPT -t filter -X || status="1"
  $IPT -t filter -P INPUT ACCEPT || status="1"
  $IPT -t filter -P OUTPUT ACCEPT || status="1"
  $IPT -t filter -P FORWARD ACCEPT || status="1"

    echo "Done."

}
case $1 in
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
  echo "Usage: sh kmyfirewall.sh { start | stop | restart } "
  ;;
  esac

if [ "$status" = "1" ]; then
  exit 1
else
  exit 0
fi
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6488&stc=1&d=1141068265[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6489&stc=1&d=1141068265[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6490&stc=1&d=1141068265[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6491&stc=1&d=1141068265[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6492&stc=1&d=1141068265[/IMG]

Thanks

---

