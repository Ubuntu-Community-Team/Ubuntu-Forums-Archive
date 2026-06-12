---
title: "Blocking Skype and other programs"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by macgyver2004 on 2010-03-03
Hello

I have wrote this code for a firewall:
```

#!/bin/sh
#deklaracja zmiennych
IPTABLES=/sbin/iptables #cieka do iptables
BLOKADA_ROUTING=1       #czy forwardowapakiety?
BLOKADA_NAT=1           #czy przekierowywac porty
BLOKADA_GG=1            #czy zablokowac GG
BLOKADA_SKYPE=1         #czy zablokowac SKYPE
BLOKADA_PROXY=1         #czy puscic HTTP przez PROXY
BLOKADA_UDP=1           #czy zablokowac UDP


if [ "$BLOKADA_ROUTING" = "1" ]; then
echo Wlaczamy routing
echo Udostepnianie internetu
echo 1 > /proc/sys/net/ipv4/ip_forward
fi

#czycimy tablicz poprzednich regu
echo Czyscimy reguly
$IPTABLES -F
$IPTABLES -X
$IPTABLES -t nat -X
$IPTABLES -t nat -F
$IPTABLES -t mangle -X
$IPTABLES -t mangle -F

if [ "$BLOKADA_NAT" = "1" ]; then
echo Przekierowanie NAT
$IPTABLES -t nat -A POSTROUTING -o eth0 -s 192.168.0.0/24 -j MASQUERADE
fi

#ustawiamy domyln polityke
echo Domyslna polityka
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP
#forwardowane porty
echo Odblokowanie portow
#21   FTP        443  HTTPS
#25   SMTP       444  SharePoint
#53   DNS        500  VPN IPSEC
#80   HTTP       1701 VPN L2TP
#81   PROXY      1723 VPN PPTP
#110  POP3       3389 MSTSC
#123  NTP        4125 OWA
#143  IMAP       4500 VPN IPSEC
#220  IMAP3      22   SSH
PORTYODB="21 22 25 53 80 81 110 143 220"
for adres in $PORTYODB
do
    echo $adres
    $IPTABLES -I FORWARD -s 192.168.0.0/24 -p tcp --dport $adres -j ACCEPT
done
PORTYODBU="53"
for adres in $PORTYODBU
do
    echo $adres
    $IPTABLES -I FORWARD -s 192.168.0.0/24 -p udp --dport $adres -j ACCEPT
done
echo Odblokowanie SSH
$IPTABLES -A INPUT --protocol tcp --destination-port 22 -j ACCEPT


if [ "$BLOKADA_UDP" = "1" ]; then
echo Ubijanie UDP
$IPTABLES -A FORWARD -s 192.168.0.0/24 -p udp --dport 1:65534 -j DROP
fi


if [ "$BLOKADA_SKYPE" = "1" ]; then
echo Ubijanie SKYPE
cat /root/banki | while read domena; do
$IPTABLES -I FORWARD 1 -d 192.168.0.0/24 -s $domena -p tcp --dport 443 -j ACCEPT
$IPTABLES -I FORWARD 1 -s 192.168.0.0/24 -d $domena -p tcp --dport 443 -j ACCEPT
done

fi

if [ "$BLOKADA_PROXY" = "1" ]; then
echo Transparetne PROXY
$IPTABLES -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 81
fi

if [ "$BLOKADA_GG" = "1" ]; then
echo Ubijanie GG
$IPTABLES -I FORWARD -i eth1 -s 192.168.0.0/24 -p tcp -d 91.197.13.0/24 -j DROP
$IPTABLES -I FORWARD -i eth1 -s 192.168.0.0/24 -p tcp -d 217.17.41.82/28 -j DROP
$IPTABLES -I FORWARD -i eth1 -s 192.168.0.0/24 -p tcp -d 217.17.45.133/27 -j DROP
$IPTABLES -I FORWARD -i eth1 -s 192.168.0.0/24 -p tcp -d 217.17.46.250/24 -j DROP
fi


```
File "/root/banki" in BLOKADA_SKYPE has adresses of banks allowed on port 443(https).
Other trafiic on 443 I want to block becouse of the Skype.

I'm trying to cut as much as i can but it didn't work.
When I use it nothing works exept www witch is through squid.
HTTPS didn't work.
There should be workinkg mail through POP,IMAP,SMTP and FTP.

---

