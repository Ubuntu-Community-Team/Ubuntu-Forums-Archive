---
title: "Help with setting up openvpn server on 8.04"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by eatont9999 on 2012-07-02
Hello folks,

I know I don't post much on here but that is because I usually find the answers to my questions by searching. I am trying to get setup an openvpn server at a remote location. I have gone through the ubuntu openvpn server tutorial but I'm not getting a response back from my server. Maybe I need to configure iptables to let port 1194 through. I allowed the port through on the router already.

I will post up my config files if anyone is interested in helping me get this VPN service setup. 

The server host is an AMD Athlon 2000 @1.67Ghz 2GB RAM. The server I am configuring is a virtual machine running off the host in VMware Server 1.0.9. Both host server and VPN server are running Hardy Heron 8.04. VPN server has the LAMP stack installed and running. Uptime:236 days.

Ubuntu openvpn tutorial:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by eatont9999 on 2012-07-02
ifconfig:

br0       Link encap:Ethernet  HWaddr 00:0c:29:a4:33:36  
          inet addr:192.168.133.14  Bcast:192.168.133.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea4:3336/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:302290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54470382 (51.9 MB)  TX bytes:112459355 (107.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:0c:29:a4:33:36  
          inet6 addr: fe80::20c:29ff:fea4:3336/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14139577 errors:1 dropped:0 overruns:0 frame:0
          TX packets:10348767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172974588 (164.9 MB)  TX bytes:4288899153 (3.9 GB)
          Interrupt:16 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1558832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1558832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:701749977 (669.2 MB)  TX bytes:701749977 (669.2 MB)

tap0      Link encap:Ethernet  HWaddr 00:ff:4d:cc:3c:42  
          inet6 addr: fe80::2ff:4dff:fecc:3c42/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:260782 (254.6 KB)

---

### Post by eatont9999 on 2012-07-02
:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
#auto lo 
#iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet static


#   address 192.168.133.14
#   netmask 255.255.255.0
#   network 192.168.133.0
#   broadcast 192.168.133.255
#   gateway 192.168.133.1



auto lo br0

iface lo inet loopback

iface br0 inet static 
  address 192.168.133.14
  netmask 255.255.255.0
  gateway 192.168.133.1
  bridge_ports eth0


iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off


  bridge_fd 9      ## from the libvirt docs (forward delay time)
  bridge_hello 2   ## from the libvirt docs (hello time)
  bridge_maxage 12 ## from the libvirt docs (maximum message age)
  bridge_stp off   ## from the libvirt docs (spanning tree protocol)

---

### Post by eatont9999 on 2012-07-02
:~$ sudo iptables -l -v
chain input (policy accept 10m packets, 2485m bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 accept     tcp  --  any    any     anywhere             anywhere            tcp dpt:openvpn 
   11   462 accept     udp  --  any    any     anywhere             anywhere            udp dpt:openvpn 
 1056  102k accept     all  --  any    any     anywhere             anywhere            state related,established 

chain forward (policy accept 1188 packets, 103k bytes)
 pkts bytes target     prot opt in     out     source               destination         

chain output (policy accept 12m packets, 9137m bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by eatont9999 on 2012-07-02
:~$ cat /etc/openvpn/server.conf 

mode server
tls-server

local 192.168.133.14 ## ip/hostname of server
port 1194 ## default openvpn port
proto udp

#bridging directive
dev tap0 ## If you need multiple tap devices, add them here
up "/etc/openvpn/up.sh br0 tap0 1500"
down "/etc/openvpn/down.sh br0 tap0"

persist-key
persist-tun

#certificates and encryption
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0 # This file is secret

cipher BF-CBC        # Blowfish (default)
comp-lzo

#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.133.10 255.255.255.0 192.168.133.100 192.168.133.150
push "dhcp-option DNS 192.168.133.10"
push "dhcp-option DOMAIN my-domain-name-here.com"

max-clients 10 ## set this to the max number of clients that should be connected at a time

#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3

---

### Post by eatont9999 on 2012-07-02
:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                   run-parts: failed to exec /etc/network/if-down.d/bfa_protection_ifdown: Exec format error
run-parts: /etc/network/if-down.d/bfa_protection_ifdown exited with return code 1

Waiting for br0 to get ready (MAXWAIT is 32 seconds).
run-parts: failed to exec /etc/network/if-up.d/bfa_protection_ifup: Exec format error
run-parts: /etc/network/if-up.d/bfa_protection_ifup exited with return code 1
 * Stopping NTP server ntpd
   ...done.
                                                                                                                                  [ OK ]
:~$  * Starting NTP server ntpd
   ...done.

---

### Post by eatont9999 on 2012-07-02
:~$ sudo /etc/init.d/openvpn restart
 * Stopping virtual private network daemon.                                                                                       [ OK ] 
 * Starting virtual private network daemon.                                                                                               * server (OK)
                                                                                                                                  [ OK ]

---

### Post by eatont9999 on 2012-07-02
Any help is appreciated. Please ask questions if you need more detail or to see a config or log file. 

Thanks!

---

