---
title: "Cannot access the internet through IPSEC/L2TP VPN"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by Blogan on 2013-04-09
On my VPS I would like to set up IPSEC/L2TP VPN. I got quite far already, setting up a VPN connection and authentication works fine. The only thing that doesn't work is to route all the internet traffic through my VPN. When I check the following box, I cannot access any internet site:

[img]http://tweakers.net/ext/f/uOkQosqoHM6Q4pOcEG5DId2M/full.png[/img]

Here are some "specs":
[list]
[*]The VPS runs on Ubuntu 12.10, I configure it using Chef Solo
[*]My client OS is Mac OS X 10.8.3, I don't have trouble to connect to other VPN's 
[*]To configure the VPN, I mostly followed this tutorial: [https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_12.10.html](https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_12.10.html)
[*]The VPS has two network interfaces: eth0 and lo. eth0 has one public IPv4-address (no private IPv4 / connected to a LAN)
[/list]
This is the output of **/var/log/syslog** after I've set up a VPN connection and when I try to connect to google.com (I replaced my own IP address and the magic code with ..., just to be sure):

```
Apr  6 12:26:07 vps1 pppd[6298]: sent [LCP ConfReq id=0x1 <mru 1000> <asyncmap 0x0> <auth pap> <magic ...> <pcomp> <accomp>]
Apr  6 12:26:07 vps1 pppd[6298]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <magic ...> <pcomp> <accomp>]
Apr  6 12:26:07 vps1 pppd[6298]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <magic ...> <pcomp> <accomp>]
Apr  6 12:26:07 vps1 pppd[6298]: rcvd [LCP ConfAck id=0x1 <mru 1000> <asyncmap 0x0> <auth pap> <magic ...> <pcomp> <accomp>]
Apr  6 12:26:07 vps1 pppd[6298]: sent [LCP EchoReq id=0x0 magic=...]
Apr  6 12:26:07 vps1 pppd[6298]: rcvd [LCP EchoReq id=0x0 magic=...]
Apr  6 12:26:07 vps1 pppd[6298]: sent [LCP EchoRep id=0x0 magic=...]
Apr  6 12:26:07 vps1 pppd[6298]: rcvd [PAP AuthReq id=0x1 user="johan" password=<hidden>]
Apr  6 12:26:07 vps1 pppd[6298]: Initializing PAM (3) for user johan
Apr  6 12:26:07 vps1 pppd[6298]: ---> PAM INIT Result = 0
Apr  6 12:26:07 vps1 pppd[6298]: Attempting PAM authentication
Apr  6 12:26:07 vps1 pppd[6298]: PAM Authentication OK for johan
Apr  6 12:26:07 vps1 pppd[6298]: Attempting PAM account checks
Apr  6 12:26:07 vps1 pppd[6298]: PAM Account OK for johan
Apr  6 12:26:07 vps1 pppd[6298]: PAM Session opened for user johan
Apr  6 12:26:07 vps1 pppd[6298]: user johan logged in on tty pts/1 intf ppp0
Apr  6 12:26:07 vps1 pppd[6298]: PAP peer authentication succeeded for johan
Apr  6 12:26:07 vps1 pppd[6298]: Unsupported protocol 'IPv6 Control Protocol' (0x8057) received
Apr  6 12:26:08 vps1 pppd[6298]: Cannot determine ethernet address for proxy ARP
Apr  6 12:26:08 vps1 pppd[6298]: local  IP address 172.16.1.1
Apr  6 12:26:08 vps1 pppd[6298]: remote IP address 172.16.1.2
Apr  6 12:27:31 vps1 pppd[6298]: LCP terminated by peer (User request)
Apr  6 12:27:31 vps1 pppd[6298]: Connect time 1.4 minutes.
Apr  6 12:27:31 vps1 pppd[6298]: Sent 0 bytes, received 82116 bytes.
Apr  6 12:27:31 vps1 xl2tpd[6215]: result_code_avp: result code endianness fix for buggy Apple client. network=768, le=3
Apr  6 12:27:31 vps1 xl2tpd[6215]: control_finish: Connection closed to ..., serial 1 ()
Apr  6 12:27:31 vps1 pppd[6298]: Modem hangup
Apr  6 12:27:31 vps1 pppd[6298]: Connection terminated.
Apr  6 12:27:31 vps1 xl2tpd[6215]: Terminating pppd: sending TERM signal to pid 6298
Apr  6 12:27:31 vps1 xl2tpd[6215]: result_code_avp: result code endianness fix for buggy Apple client. network=256, le=1
Apr  6 12:27:31 vps1 xl2tpd[6215]: control_finish: Connection closed to ..., port 52547 (), Local: 26551, Remote: 37
Apr  6 12:27:31 vps1 pppd[6298]: Terminating on signal 15
Apr  6 12:27:31 vps1 pppd[6298]: Exit.
Apr  6 12:27:31 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:31 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:33 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:33 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:37 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:37 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:41 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:41 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:46 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:46 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:50 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:50 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:54 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
Apr  6 12:27:54 vps1 xl2tpd[6215]: network_thread: unable to find call or tunnel to handle packet.  call = 2596, tunnel = 26551 Dumping.
Apr  6 12:27:58 vps1 xl2tpd[6215]: Can not find tunnel 26551 (refhim=0)
```

Because the VPS has no LAN and I need to hand out an IP-address to each VPN connection (I believe), I created a new loopback interface. I'm not sure if it's the right method, but this is how **/network/interfaces** looks like:

```
auto lo lo:10
iface lo inet loopback

dns-nameservers 164.138.29.5 164.138.29.6

auto eth0
iface eth0 inet static
        address <public IP-address of the VPN>
        netmask 255.255.255.0
        gateway 164.138.29.1
        hwaddr ether <MAC-address>

iface lo:10 inet static
        address 172.16.1.1
        network 172.16.1.0
        netmask 255.255.255.0
```

**/etc/iptables/rules.v4** has the following content (for this I use iptables-persistent):

```
# Generated by iptables-save v1.4.12 on Fri Apr  5 22:38:12 2013
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [26212:1633690]
-A INPUT -i lo -j ACCEPT
-A INPUT -i lo:10 -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p udp -m udp --dport 4500 -j ACCEPT
-A INPUT -p udp -m udp --dport 500 -j ACCEPT
-A INPUT -p udp -m policy --strict --dir in --pol ipsec --proto esp -m udp --dport 1701 -j ACCEPT
-A INPUT -m policy --strict --dir in --pol ipsec --proto esp -j REJECT
-A INPUT -j DROP
COMMIT
# Completed on Fri Apr  5 22:38:12 2013
# Generated by iptables-save v1.4.12 on Fri Apr  5 22:38:12 2013
*nat
:PREROUTING ACCEPT [3:96]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [12:776]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -j MASQUERADE
COMMIT
# Completed on Fri Apr  5 22:38:12 2013
```

And here's an overview of some other configuration files.

**/etc/ipsec.conf**:
```
config setup
    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.1.0/24,%v6:fd00::/8,%v6:fe80::/10
    oe=off
    protostack=netkey

conn %default
    forceencaps=yes

conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    ikelifetime=8h
    keylife=1h
    type=transport
    left=<public IP-address of the VPN>
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
    dpddelay=30
    dpdtimeout=60
    dpdaction=clear


```

**/etc/ppp/options.xl2tpd**:
```
login
ms-dns 8.8.8.8
ms-dns 8.8.4.4
auth
mtu 1200
mru 1000
crtscts
hide-password
modem
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
```

**/etc/xl2tpd/xl2tpd.conf**:
```
[global]
ipsec saref = yes

[lns default]
ip range = 172.16.1.2-172.16.1.254
local ip = 172.16.1.1
unix authentication = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes
```

**/etc/sysctl.conf**:
```
net.ipv4.ip_forward = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.lo.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.eth0.send_redirects = 0
```

**/etc/pam.d/ppp**:
```
auth    required        pam_nologin.so
auth    required        pam_unix.so
account required        pam_unix.so
session required        pam_unix.so
```

**/etc/ppp/pap-secrets**:
```
*       l2tpd           ""              *
```

I did a few more checks..

**sudo ipsec verify** gives the following result:

[img]http://tweakers.net/ext/f/Yiiuu9JCbqYWIwJEgkTTX6VP/full.png[/img]

When I connect to the VPS through SSH, I have no problems to ping the outer world:

```
ping -c 3 google.com
PING google.com (173.194.66.139) 56(84) bytes of data.
64 bytes from we-in-f139.1e100.net (173.194.66.139): icmp_req=1 ttl=50 time=5.22 ms
64 bytes from we-in-f139.1e100.net (173.194.66.139): icmp_req=2 ttl=50 time=5.16 ms
64 bytes from we-in-f139.1e100.net (173.194.66.139): icmp_req=3 ttl=50 time=4.91 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 4.914/5.100/5.225/0.157 ms
```

This is what **ifconfig** returns after I've set up a VPN connection (replaced public IP-address with ...):

```
vps1% ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4a:7d:d1:1b  
          inet addr:...  Bcast:164.138.29.255  Mask:255.255.255.0
          inet6 addr: ... Scope:Global
          inet6 addr: ... Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:195788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28371480 (28.3 MB)  TX bytes:13302626 (13.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10506681 (10.5 MB)  TX bytes:10506681 (10.5 MB)

lo:10     Link encap:Local Loopback  
          inet addr:172.16.1.1  Mask:255.255.255.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.16.1.1  P-t-P:172.16.1.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1000  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3563 (3.5 KB)  TX bytes:85 (85.0 B)

```

Hopefully someone can help me with setting it up correctly :)

---

### Post by teegee543 on 2013-04-11
I had the same problem with the "Can not find tunnel" error and figured out that it was because of an incorrect route in iptables.
Not sure how to set this up in iptables-persistent, but try this:

/etc/rc.local (add right before last line saying "exit 0":
```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 172.16.1.0/24 -o eth0 -j MASQUERADE
```

Then to enable the new rules without restarting:
```
sudo /etc/rc.local
```

---

### Post by Blogan on 2013-04-11
Thanks a lot for your reply :)

I have tried to add that to rc.local, but it didn't help, unfortunately. I've also tried to remove all firewall rules using this script:

```
#!/bin/sh
echo "Stopping firewall and allowing everyone..."
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

After that, I tried running your commands (with sudo sh /etc/rc.local), but no result. I get the same "Can not find tunnel" errors. I also tried masquerading lo:10 and ppp0, but no luck.

My feeling says it has something to do with the loopback interface I created. I'm not sure if that's the right way to do it. Any help is welcome!

---

### Post by Blogan on 2013-04-25
*bump* Would really appreciate it if someone could point me in the right direction! :)

---

