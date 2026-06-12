---
title: "IPTABLES rule"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by williamwd on 2011-08-10
Hello,

i've a problem in my LAN, where i can simply plug a cable on unauthorized computers and, setting manually the IP address and other stuff, i am able to open websites normally.
I've been searching on the web alternatives to make this impossible with IPTABLES, but i found a way to do this with SQUID3, but i do not want this way, since the user can still use messengers and other stuff.
Is there a way to block unwanted MAC addresses using IPTABLES?

My rules:[INDENT]```


#!/bin/bash

#/etc/init.d/bind9 restart
#/etc/init.d/squid3 restart
#/etc/init.d/networking restart
/etc/init.d/isc-dhcp-server restart
/etc/init.d/shaper restart

# load 
/sbin/modprobe iptable_nat
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ipt_LOG
/sbin/modprobe ipt_REJECT
/sbin/modprobe ipt_MASQUERADE

# protecao contra spoofing
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter

# protecao contra spoofing 2
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses

# limpa as tabelas existentes
iptables -F
iptables -t mangle -F
iptables -t nat -F
iptables -X

# politica padrao
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# conexoes preestabelecidas
iptables -A INPUT -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT

# libera interface loopback
iptables -A INPUT -i lo -j ACCEPT

# Registro de logs
iptables -A INPUT -p tcp --dport 333 --syn -j LOG --log-prefix="[TENTATIVA ACESSO FWLOGWATCH]"
iptables -A INPUT -p tcp --dport 23 --syn -j LOG --log-prefix="[TENTATIVA ACESSO TELNET]"
#iptables -A INPUT -p tcp --dport 10000 --syn -j LOG --log-prefix="[TENTATIVA ACESSO WEBMIN]"
#iptables -A FORWARD -m multiport -p tcp --dport 5800,5900,6000 -j LOG --log-prefix="[ACESSO VNC]"
#iptables -A INPUT -p tcp --dport 22 --syn -j LOG --log-prefix="[TENTATIVA ACESSO SSH]"
iptables -A INPUT -p tcp --dport 2222 --syn -j LOG --log-prefix="[TENTATIVA ACESSO SSH]"
iptables -A INPUT -p tcp --dport 21 --syn -j LOG --log-prefix="[TENTATIVA ACESSO FTP]"

############### Redireciona pro Squid #############################
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128


#################################### SCRIPT ####################################################
#Declarando algumas variaveis
arq_clientes="/home/william/PHP/cadastro/cadastro.txt"
for ip in `cat $arq_clientes|cut -d# -f 1` ; do
    # Identifica o MAC ADDRESS
    mac="`grep -w $ip $arq_clientes|cut -d# -f2`"
    # Identifica o nome do cliente
    cliente="`grep -w $ip $arq_clientes|cut -d# -f3`"
        bloq="`grep -w $ip $arq_clientes|cut -d# -f4`"
    #echo "#################"
          #echo -e "Cadastrou o IP: $ip\nMAC: $mac\nCLIENTE: $cliente"

############## tried this way but it just doesn't work

#      iptables -t filter -A FORWARD -d 0/0 -s $ip -m mac --mac-source ! $mac -j DROP
#          iptables -t filter -A FORWARD -d $ip -s 0/0 -m mac --mac-source ! $mac -j DROP 
#      iptables -t nat -A INPUT -s $ip -d 0/0 -m mac --mac-source ! $mac -j REJECT

################################################

          iptables -t filter -A FORWARD -d 0/0 -s $ip -m mac --mac-source $mac -j ACCEPT
          iptables -t filter -A FORWARD -d $ip -s 0/0 -m mac --mac-source $mac -j ACCEPT
          iptables -t filter -A INPUT -s $ip -d 0/0 -m mac --mac-source $mac -j ACCEPT
      iptables -t nat -A POSTROUTING -s $ip -o ppp0 -j MASQUERADE
done
################################################################################################

# habilita roteamento no kernel
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Done."

```
[/INDENT]
PS: Sorry for the bad english, i still need some practice :???:

---

