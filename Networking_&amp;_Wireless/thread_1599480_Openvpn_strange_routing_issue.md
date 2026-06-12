---
title: "Openvpn strange routing issue"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by metallica1973 on 2010-10-17
I have setup openvpn on the server using ubuntu 9.04 and my client can connect but with issues. His network is very little and consisting of 7 computers including his POS system and his own computer. His network also has 5 IP cameras. His internal network is a 10.255.1.X. The VPN network is setup to 10.255.2.X. His POS IP range is 10.255.1.1 through 10.255.1.6 and his IP cameras are 10.255.1.160 through 10.255.1.164. When connecting through the VPN, I can ping the cameras perfectly fine but I cannot connect to them. I cant ping the gateway which is 10.255.1.200(Netgear FVS318 Firewall) or any other computer other then the cameras. So when connecting I can only ping the cameras but I cant ping or connect to anything else. Here are the configs on the server:

[PHP]dev tun
    proto tcp
    port 1723

    ca /etc/openvpn/keys/ca.crt
    cert /etc/openvpn/keys/server.crt
    key /etc/openvpn/keys/server.key
    dh /etc/openvpn/keys/dh1024.pem

    #user nobody
    #group nogroup
    server 10.255.2.0 255.255.255.0
    ifconfig-pool-persist ipp.txt
    push "dhcp-option DNS 10.255.1.200"
    push "route 10.255.1.0 255.255.255.0"
    persist-key
    persist-tun

    #status openvpn-status.log
    #verb 3
    client-to-client
    duplicate-cn
    keepalive 10 120
    max-clients 2
    user nobody
    group nogroup
    verb 3
    comp-lzo  [/PHP]

and here is my client.conf:

[PHP]client
    remote client
    ;dev tap
    dev tun
    ;dev-node MyTap
    proto tcp
    
    remote kurutemizleme.dyndns.info 1723
    ;remote my-server-2 1194
    ;remote-random
    ns-cert-type server
     resolv-retry infinite
    nobind
    user nobody
    group nogroup
    persist-key
    persist-tun
    ;http-proxy-retry # retry on connection failures
    ;http-proxy [proxy server] [proxy port #]
    ;mute-replay-warnings
    ca /etc/openvpn/certs/ca.crt 
    cert /etc/openvpn/certs/laptop.crt
    key /etc/openvpn/certs/laptop.key
    ;ns-cert-type server
    ;tls-auth ta.key 1
    ;cipher x
    comp-lzo
    verb 3
    route-method exe
    route-delay 2
    ;mute 20  [/PHP]

Here is my ping results after I connect to the network. I have used this same config on other networks with no problem at all. I had to make a couple of firewall changes but at this site I cant figure it out. There are using a Netgear FVS318 Firewall/Router. I am thinking that it may be the issue. As you can see I cannot ping the router(10.255.1.200), nor any node (10.255.1.1-6) just the cameras(10.255.1.160-164). ?????????????

[PHP]test@Dartanion:~$ ping 10.255.1.1
PING 10.255.1.1 (10.255.1.1) 56(84) bytes of data.
^C
--- 10.255.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

test@Dartanion:~$ ping 10.255.1.2
PING 10.255.1.2 (10.255.1.2) 56(84) bytes of data.
^X^C
--- 10.255.1.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

test@Dartanion:~$ ping 10.255.1.160
PING 10.255.1.160 (10.255.1.160) 56(84) bytes of data.
64 bytes from 10.255.1.160: icmp_seq=1 ttl=63 time=72.2 ms
^C
--- 10.255.1.160 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 72.210/72.210/72.210/0.000 ms
test@Dartanion:~$ ping 10.255.1.161
PING 10.255.1.161 (10.255.1.161) 56(84) bytes of data.
64 bytes from 10.255.1.161: icmp_seq=1 ttl=63 time=52.3 ms
^C
--- 10.255.1.161 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 52.358/52.358/52.358/0.000 ms
test@Dartanion:~$ ping 10.255.1.200
PING 10.255.1.200 (10.255.1.200) 56(84) bytes of data.
^C
--- 10.255.1.200 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1010ms  [/PHP]

---

### Post by joris1977 on 2010-10-18
I am very new to openvpn and maybe not much of a help and I stumbled over your post,because I was having similar problems....

The openvpn site is a great resource of information, but not really simple for a non-technical person like me 

That said: 

Most of the times a firewall seems to be the problem. (seemed to be the problem also in my case.)

[http://openvpn.net/index.php/open-source/faq/77-server/263-openvpn-can-ping-both-peers-but-i-cant-reach-any-of-the-other-machines-on-the-remote-subnet.html](http://openvpn.net/index.php/open-source/faq/77-server/263-openvpn-can-ping-both-peers-but-i-cant-reach-any-of-the-other-machines-on-the-remote-subnet.html)

I am not very good with iptables.

Maybe the solution is to forward all trafic from the virtual ip to the lan

After some googling on the openvpn site I think this might be a solution...

iptables -A FORWARD -i tun0 -s 10.255.2.0/24 -d 10.255.1/24 -j ACCEPT

---

### Post by metallica1973 on 2010-10-18
many thanks but how would I do that on a NETGEAR FS318 router?

---

### Post by metallica1973 on 2010-10-19
you were correct and many thanks for your direction. Issue Resolved:

It was in fact the NETGEAR FVS318 Router that was the root cause of my issues. I was under the impression that the VPN passthrough was all that was needed to allow the proper routing between subnets. That wasnt the case and I needed to add a static route on the NETGEAR FVS318 Firewall/Router to pass traffic to all the other subnets ----10.255.1.0 through the router:

10.255.2.0(VPN Network) ------> 10.255.1.180(VPN Server) --static route on NETHEAR FVS318

Works Perfectly.

---

