---
title: "iptables and check script"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by nid3 on 2009-06-06
hello
I'm interesting what are U think about my iptables script. I have apache server on my notebook and I use a bittorrent protocol. I think it is a good script but i would like hear Yours opinions on security to siplly laptop.
```
################################################
##############################
iptables -F
#################################################
#### polityka DROP dla INPUT
 iptables -P INPUT DROP
#################################################
#### polityka DROP dla OUTPUT
 iptables -P OUTPUT DROP
###################################################
#### polityka ACCEPT dla FORWARD
 iptables -P FORWARD ACCEPT

#### wlaczenie loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A FORWARD -o lo -j ACCEPT 



#####################################################################
####### WWW  & DNS ##################################################

iptables -A OUTPUT -p tcp  --syn -s $ip  --dport 80 -j ACCEPT -m state --state NEW
iptables -A OUTPUT -p udp  -s $ip  --dport 53 -j ACCEPT -m state --state NEW

#####################################################################
####### kadu ########################################################

iptables -A OUTPUT -p tcp -s 0/0 --dport 8074 -j ACCEPT -m state --state NEW

####################################################################
###### ssh -logowanie 1 na minute- #################################
#iptables -A INPUT -p tcp --dport 22 -m limit --limit 1/min 
#iptables -A INPUT -p tcp --dport 22 -m hashlimit --hashlimit 1/min --hashlimit-mode srcip --hashlimit-name ssh -m state --state NEW -j ACCEPT
 iptables  -A  INPUT  -p  tcp   --dport  22  -m   connlimit --connlimit-above 1 -j REJECT
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT -m state --state NEW

####################################################################
##### auth #########################################################

iptables -A INPUT -p tcp --source-port 113 -j ACCEPT

#####################################################################
#### ftp  ###########################################################

#iptables -A INPUT -p tcp ! --syn --sport 20:21 -d $ip --dport 1024:65535 -j ACCEPT
iptables -A OUTPUT -p tcp -s $ip --sport 1024:65535 --dport 20:21 -j ACCEPT -m state --state NEW

######################################################################
#### Zabezpieczenie przed powodzia SYN (Syn-flood):###################

iptables -A INPUT -p tcp --syn -m limit --limit 1/s -j ACCEPT

######################################################################
#### Ping of death: ##################################################

iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

#####################################################################
#### Wlaczenie przekazywania IP######################################

echo 1 > /proc/sys/net/ipv4/ip_forward

#####################################################################
#### Wlaczenie blokady komunikatow echo (ping) jesli : 0 --true  , 1 --false

echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all

#####################################################################
#### Blokada przed atakami typu SYN FLOODING

echo 1 > /proc/sys/net/ipv4/tcp_syncookies

#####################################################################
# Weryfikacja adresu zrodlowego na poziomie kernela
# zeby zdalne hosty nie mogly sie podszyc pod moj komputer
#####################################################################

echo 1 > /proc/sys/net/ipv4/conf/default/rp_filter

################################################
#PING
iptables -A INPUT -p icmp -s 0/0 -d 0/0 -j DROP

####################################################################
####  https, skype, apache ######################################

iptables -A OUTPUT -p tcp -s $ip --sport 1024:65535 --dport 443 -j ACCEPT -m state --state NEW

#############################################################################

iptables -A OUTPUT  -p tcp -s $ip -d 0/0 --dport 1024:65535 -j ACCEPT -m state --state NEW

#############################################################################
#############################################################################

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp -m state --state ESTABLISHED -j ACCEPT

iptables -A INPUT -m state --state INVALID -j DROP
``` 

thx for all answers:)

---

