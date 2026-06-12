---
title: "Subnet/Proxy router with iptables and sharing internet connection from subnet1 to 2"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by emarques on 2009-08-14
Hello all, I hope someone can be of assistence since I've searched and googled for troubleshooting information everywhere and can't seem to find an answer to my problem.

I have a Ubuntu 8.04 machine serving as proxy/gatewat/dhcp in subnet 2 and connecting subnet 2 to subnet 1 which has its own firewall/gateway from which internet connection is served.

I have successfully connected the 2 subnets - and computers on one side can see computers on the other side and so on. Internet connection is also available on both subnets, though on subnet 2 the internet connection icon does not appear on windows vista.

So far everything seemed ok, but we are getting many network errors from subnet2 (when communicating with subnet1), thus interfering with printing, access to corporate software located on servers in subnet1 randomic failures, sometimes we can't open files located in subnet1 (have to copy them to desktop for example to work with those files), etc.

Here follows nic configuration and iptables rules:

_ifconfig_

```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:72:4c:a8
          inet addr:10.80.116.253  Bcast:10.80.116.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe72:4ca8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13986609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12700183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1402602250 (1.4 GB)  TX bytes:2438311937 (2.4 GB)
          Interrupt:220 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:1a:3f:4b:97:ea
          inet addr:10.85.116.254  Bcast:10.85.116.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:3fff:fe4b:97ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11743273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12461215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2379925825 (2.3 GB)  TX bytes:829115466 (829.1 MB)
          Interrupt:21 Base address:0xd000
```

_route -n_
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.80.116.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.85.116.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.80.116.254   0.0.0.0         UG    100    0        0 eth0
```

_iptables script_

```
# Local para o executavel do IPTables
IPT=`which iptables`;

# Interfaces de Rede
IF_SERVIDORES="eth0"; # Interface dos servidores
IF_ESTACOES="eth1"; # Interface das estacoes

# Definicao das redes
REDE_ESTACOES="10.85.116.1/24";
REDE_SERVIDORES="10.80.116.1/24";

# Maquina liberada
GER="10.85.116.18"

# INICIO DAS REGRAS
start()
{
  echo
  echo "INICIANDO O FIREWALL..."
  echo

  # Ativa o roteamento dinamico
  echo "- Ativando roteamento dinamico..."
    echo 1 > /proc/sys/net/ipv4/ip_forward
    echo 1 > /proc/sys/net/ipv4/ip_dynaddr

  # Carrega todos os modulos necessarios
  echo "- Ativando modulos..."
  /sbin/modprobe iptable_nat
  /sbin/modprobe ip_conntrack
  /sbin/modprobe ip_conntrack_ftp
  /sbin/modprobe ip_nat_ftp
  /sbin/modprobe ipt_LOG
  /sbin/modprobe ipt_REJECT
  /sbin/modprobe ipt_MASQUERADE

  # Protecao contra IP Spoofing
  echo "- Protecao contra IP Spoofing..."
  echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter

  # Zera regras
  echo "- Zerando regras..."
  $IPT -F
  $IPT -X
  $IPT -F -t nat
  $IPT -X -t nat
  $IPT -F -t mangle
  $IPT -X -t mangle

    # ================ POLITICAS PADRAO ===================
    echo "- Ativando politicas padrao..."
#    $IPT -P INPUT       DROP
#    $IPT -P FORWARD     DROP
    $IPT -P INPUT       ACCEPT
    $IPT -P FORWARD     ACCEPT
    $IPT -P OUTPUT      ACCEPT
    $IPT -t nat    -P PREROUTING  ACCEPT
    $IPT -t nat    -P POSTROUTING ACCEPT
    $IPT -t nat    -P OUTPUT      ACCEPT
    $IPT -t mangle -P PREROUTING  ACCEPT
    $IPT -t mangle -P POSTROUTING ACCEPT
    $IPT -t mangle -P OUTPUT      ACCEPT
    $IPT -t mangle -P INPUT       ACCEPT
    $IPT -t mangle -P FORWARD     ACCEPT

# Cria chain com regras de seguranca
#  echo "* Criando regras de seguranca..."
#  $IPT -N BLOCK
#  $IPT -A BLOCK -p icmp --icmp-type echo-request -j DROP
#  $IPT -A BLOCK -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
#  $IPT -A BLOCK -p tcp -m limit --limit 1/s -j ACCEPT
#  $IPT -A BLOCK -p tcp --tcp-flags SYN,ACK,RST SYN,FIN -m limit --limit 1/s -j ACCEPT
#  $IPT -A BLOCK -m state --state ESTABLISHED,RELATED -j ACCEPT
#  $IPT -A BLOCK -j LOG --log-prefix "FW_ALERT: "
#  $IPT -A BLOCK -j DROP

# Protecao contra Syn-floods
#  echo "* Protecao contra Syn-floods..."
#  $IPT -A FORWARD -p tcp --syn -m limit --limit 1/s -j ACCEPT

# Port scanners ocultos
#  echo "* Port scanners ocultos..."
#  $IPT -A FORWARD -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/s -j ACCEPT

#
# PROXY / SQUID (No proxy configured)
#
 echo "* Ativando regras para o proxy...."
 $IPT -t nat -A PREROUTING -s ! 10.85.116.254 -d ! 189.21.233.19 -p tcp --dport 80 -j DNAT --to 10.85.116.254:80 # o IP 189.21.233.19 e' da ANS

#
# BLOQUEIO DO MSN e PERMISSAO DO MSN PARA O SRV 152
#
 echo "* Bloqueando MSN na rede..."
 $IPT -A FORWARD -p tcp --dport 1863 -j DROP
 $IPT -A FORWARD -d 207.46.100.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.101.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.102.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.103.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.104.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.105.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.106.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.107.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.108.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.109.0/25 -j DROP
 $IPT -A FORWARD -d 207.46.110.0/25 -j DROP

#
# ENCAMINHAMENTO PARA O ULTRA VNC - SUPORTE REMOTO COM OS PRESTADORES
#
$IPT -t nat -A PREROUTING -p tcp --dport 5500 -j DNAT --to 10.85.116.12:5500
$IPT -I FORWARD -s 10.85.116.12 -p tcp --dport 5500 -j ACCEPT

#
# BLOQUEIO DO ORKUT
#
 echo "* Bloqueando Orkut na rede..."
 $IPT -I INPUT -s ! $GER -d ! $GER -j DROP -p tcp -m string --string "orkut" --algo bm
 $IPT -s ! $GER -A FORWARD -d 72.14.247.85 -j DROP
 $IPT -s ! $GER -A FORWARD -d 72.14.209.85 -j DROP
 $IPT -s ! $GER -A FORWARD -d 209.85.141.85 -j DROP

# Libera todo o trafego local
 echo "* Liberando trafego local..."
 $IPT -t filter -A INPUT   -i lo -j ACCEPT
 $IPT -t filter -A FORWARD -i lo -j ACCEPT
 $IPT -t filter -A OUTPUT -j ACCEPT

 $IPT -t filter -A INPUT   -i $IF_ESTACOES -j ACCEPT
 $IPT -t filter -A FORWARD -i $IF_ESTACOES -j ACCEPT
#teste
 $IPT -t filter -A INPUT   -i $IF_SERVIDORES -j ACCEPT
 $IPT -t filter -A FORWARD -i $IF_SERVIDORES -j ACCEPT

# Liberacao de portas de comunicacao
# echo "* Liberando portas de comunicacao..."
 $IPT -t filter -A INPUT -i $IF_ESTACOES -p tcp -m multiport --dports 21:59999 -j ACCEPT
 $IPT -t filter -A FORWARD -i $IF_ESTACOES -p tcp -m multiport --dports 21:59999 -j ACCEPT

# Libera a conexao para a rede interna
 echo "* Liberacao de conexoes para a rede interna (Servidores e Estacoes)..."
 $IPT -t nat -A POSTROUTING -o $IF_SERVIDORES -j MASQUERADE

# ============ FIREWALL ATIVO! ==============
 echo
 echo "FIREWALL ATIVO!"
 echo

```

Can anyone provide help? :confused:

Thanks.
Eduardo.

---

### Post by superprash2003 on 2009-08-14
are machines able to ping each other from subnet 1 to subnet 2 and vice versa?

---

### Post by emarques on 2009-08-14
Yes. We can ping subnet2 from computers in subnet1 and vice versa.

This is how the network is distributed:

 ```
                             Internet
                                  |
                                  |
                       /-----------------------/
                       /       Firewall        /
                       / (Gateway for subnet1) /
                       /-----------------------/
                                  |
                              ----------
                              * Switch *
                              ----------
                               |      |
                       -----------  /------------------/
                       | subnet1 |  /   Proxy/Router   /
                       -----------  / (GW for subnet2) /
                                    /------------------/
                                              |
                                          -----------
                                          | subnet2 |
                                          -----------
```

There is a route added in the internet firewall (GW for subnet1) to route packets for network 10.85.116.0 through network ip 10.80.116.253 (the ip address of nic eth0 on the proxy/router).

Ping, Internet, Aplications, Network shares, etc... everything is working on both subnets... but we are facing randomic network errors on subnet2... like aplication crash, failure to read network files, like word and excel files.. (but if you copy/past to desktop they can be read without any problems), failure to print (example.. you send a 10 page document to a printer on subnet1 and it only prints 2 pages...), windows update not working right.. windows networking icon not showing internet connection, etc..

I don't know exactly why those network problems happen... my best guess is that I'm missing something in iptables rules of the proxy/router..?

---

