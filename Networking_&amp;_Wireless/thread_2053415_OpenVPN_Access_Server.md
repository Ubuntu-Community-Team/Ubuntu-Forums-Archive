---
title: "OpenVPN Access Server"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by saltydk on 2012-09-05
Trying to use port 123 UDP and have supposedly uninstalled the NTP daemon that previously used the port but no connection can be made when I listen the server on this port whilst it works fine on other ports.

Is there some way of "opening" up this port? Using Ubuntu 11.04.

---

### Post by The Cog on 2012-09-05
For a start, let's see if the port is open, and if so by which process. Try the command
```
sudo netstat -lnpu
```

Unless you blocked access to the port by installing a firewall yourself, the only action needed to "open" a port is to start the appropriate service/daemon. We could have a look at your iptables rules to make sure it's not being blocked. Post the output of this command:
```
sudo iptables -nvL
```

---

### Post by saltydk on 2012-09-05
```
(root@Y053)-(~) $ sudo netstat -lnpu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           717/avahi-daemon: r
udp        0      0 0.0.0.0:38565           0.0.0.0:*                           717/avahi-daemon: r
udp        0      0 x.x.x.x:123       0.0.0.0:*                           18947/openvpn
udp6       0      0 :::5353                 :::*                                717/avahi-daemon: r
udp6       0      0 :::36976                :::*                                717/avahi-daemon: r
(root@Y053)-(~) $


Chain INPUT (policy ACCEPT 51 packets, 2663 bytes)
 pkts bytes target     prot opt in     out     source               destination
 5397 2326K AS0_ACCEPT  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    0     0 AS0_ACCEPT  all  --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 AS0_IN_PRE  all  --  *      *       0.0.0.0/0            0.0.0.0/0           mark match 0x2000000/0x2000000
   17  2248 AS0_ACCEPT  udp  --  *      *       0.0.0.0/0            x.x.x.x       state NEW udp dpt:123
    0     0 AS0_WEBACCEPT  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    2   104 AS0_WEBACCEPT  tcp  --  *      *       0.0.0.0/0            x.x.x.x       state NEW tcp dpt:943
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:123

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 AS0_ACCEPT  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    0     0 AS0_IN_PRE  all  --  *      *       0.0.0.0/0            0.0.0.0/0           mark match 0x2000000/0x2000000
    0     0 AS0_OUT_S2C  all  --  *      as0t+   0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT 9208 packets, 13M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 AS0_OUT_LOCAL  all  --  *      as0t+   0.0.0.0/0            0.0.0.0/0

Chain AS0_ACCEPT (4 references)
 pkts bytes target     prot opt in     out     source               destination
 5414 2328K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_IN (4 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            5.5.0.1
    0     0 AS0_IN_POST  all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_IN_POST (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 AS0_OUT    all  --  *      as0t+   0.0.0.0/0            0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_IN_PRE (2 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            5.5.0.0/20
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            192.168.0.0/16
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            172.16.0.0/12
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            10.0.0.0/8
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_OUT (2 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_OUT_LOCAL (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 5
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_OUT_S2C (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 AS0_OUT    all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain AS0_WEBACCEPT (2 references)
 pkts bytes target     prot opt in     out     source               destination
    2   104 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

---

### Post by saltydk on 2012-09-05
It looks like it is "open" does it not?

---

### Post by The Cog on 2012-09-05
I don't see anything wrong there. I can see that openvpn is indeed listening on port 123, and I can see that 17 new connections to that port have been accepted by iptables.

Actually, your firewall doesn't seem to be doing a lot to me. It has a default policy to accept all incoming connections, and although it could block some outgoing connections (those leaving via interface as0t+) is hasn't blocked any. Maybe I'm missing something?

Your post contains the machine's public IP address (in 3 places). You may want to edit your post and remove that.

My next step would be to double-check with tcpdump, and look at the openvpn log to see what's going on. The command
```
sudo tcpdump udp port 123
```
will show packets arriving and leaving using that port. We can see from iptables that packets are arriving on the interface, but I would check whether openvpn is sending reply packets.

---

### Post by saltydk on 2012-09-05
When using sudo tcpdump udp port 123 I get activity as soon as I try to initiate a connection from my client. From what I gather it looks like the server does send some manner of reply back.

As for the firewall I think I disabled that in the process of eliminating stuff that could interfere. My knowledge regarding Linux in general is limited however so may not have done it correctly.

I'll do some tests and see if its all UDP ports that it is having trouble with. Think I had TCP+UDP failover enabled, in case UDP was blocked by the client.

---

### Post by saltydk on 2012-09-05
Have no problems connecting to the server from any other UDP port I have tried since my last post. Seeing as I get some response from the sudo tcpdump udp port 123 command earlier its safe to assume that the port itself is not blocked by the network host?

---

### Post by saltydk on 2012-09-05
I just found something that may shed some light. Not sure if it matters but here goes:

UDP 123 connection attempt (client GUI of OpenVPN shows no responce)
```
14:36:43.266607 IP myclient.58422 > myserver.ntp: NTPv7, unspecified, length 42
14:36:43.267317 IP myserver.ntp > myclient.58422: NTPv0, unspecified, length 54
14:36:43.311646 IP myclient.ntp > myserver.ntp: NTPv5, unspecified, length 50
14:36:43.313075 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:43.314187 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:43.314584 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 52
14:36:45.338913 IP myserver.ntp > myclient.58422: NTPv0, unspecified, length 42
14:36:45.372815 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:46.402486 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:47.432202 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 52
14:36:49.456527 IP myserver.ntp > myclient.58422: NTPv0, unspecified, length 42
14:36:49.493250 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:50.522984 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:51.552736 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 52
14:36:57.629425 IP myserver.ntp > myclient.58422: NTPv0, unspecified, length 42
14:36:58.143091 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:58.144316 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 142
14:36:59.274313 IP myclient.ntp > myserver.ntp: NTPv4, unspecified, length 52
14:37:13.462022 IP myserver.ntp > myclient.58422: NTPv0, unspecified, length 42

```

Now on UDP 45321
```
14:52:38.580459 IP myclient.49820 > myserver.45321: UDP, length 42
14:52:38.581210 IP myserver.45321 > myclient.49820: UDP, length 54
14:52:38.625571 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.626474 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.626586 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.627795 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.627907 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.628275 IP myclient.49820 > myserver.45321: UDP, length 52
14:52:38.629612 IP myserver.45321 > myclient.49820: UDP, length 154
14:52:38.629628 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.629639 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.629650 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.672967 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.673114 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.673793 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.673940 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.674315 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.674463 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.675291 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.675439 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.716650 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.716800 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.718431 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.718578 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.719009 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.719156 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.720176 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.720324 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.759830 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.759979 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.761801 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.761952 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.762748 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.762894 IP myserver.45321 > myclient.49820: UDP, length 61
14:52:38.763520 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.802919 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.805545 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.811348 IP myclient.49820 > myserver.45321: UDP, length 154
14:52:38.811508 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.812697 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.812848 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.813669 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.813818 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.815266 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.815431 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.856198 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.856347 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.857348 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.857497 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.858112 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.858261 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.860802 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.860951 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.899744 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.899896 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.901194 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.901654 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.902689 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.903721 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.905095 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:38.905397 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:38.943565 IP myclient.49820 > myserver.45321: UDP, length 83
14:52:38.943923 IP myserver.45321 > myclient.49820: UDP, length 154
14:52:38.943943 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.943953 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.943964 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.987239 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.987384 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.987982 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.988124 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:38.988731 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:38.988873 IP myserver.45321 > myclient.49820: UDP, length 124
14:52:38.989424 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:39.031218 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:39.031632 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:39.034991 IP myclient.49820 > myserver.45321: UDP, length 154
14:52:39.035146 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:39.036267 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:39.036411 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:39.037237 IP myclient.49820 > myserver.45321: UDP, length 142
14:52:39.037380 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:39.037933 IP myclient.49820 > myserver.45321: UDP, length 88
14:52:39.038391 IP myserver.45321 > myclient.49820: UDP, length 154
14:52:39.038421 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:39.038444 IP myserver.45321 > myclient.49820: UDP, length 124
14:52:39.082117 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:39.082892 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:39.083279 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:41.351914 IP myclient.49820 > myserver.45321: UDP, length 132
14:52:41.352185 IP myserver.45321 > myclient.49820: UDP, length 50
14:52:41.352205 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:41.352215 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:41.352225 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:41.352235 IP myserver.45321 > myclient.49820: UDP, length 142
14:52:41.396087 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:41.396230 IP myserver.45321 > myclient.49820: UDP, length 116
14:52:41.396499 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:41.397112 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:41.397770 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:43.429051 IP myserver.45321 > myclient.49820: UDP, length 116
14:52:47.491317 IP myserver.45321 > myclient.49820: UDP, length 116
14:52:48.085306 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:48.086226 IP myclient.49820 > myserver.45321: UDP, length 53
14:52:48.086925 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:48.087704 IP myclient.49820 > myserver.45321: UDP, length 50
14:52:48.088635 IP myclient.49820 > myserver.45321: UDP, length 165
14:52:48.089659 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.090355 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.091346 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.092065 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.092811 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.093598 IP myclient.49820 > myserver.45321: UDP, length 101
14:52:48.094133 IP myclient.49820 > myserver.45321: UDP, length 93
14:52:48.095264 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.096051 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.097285 IP myclient.49820 > myserver.45321: UDP, length 197
14:52:48.098784 IP myclient.49820 > myserver.45321: UDP, length 197
14:52:48.099571 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.100477 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.101229 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.102193 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.104692 IP myclient.49820 > myserver.45321: UDP, length 469
14:52:48.105634 IP myclient.49820 > myserver.45321: UDP, length 133
14:52:48.106742 IP myclient.49820 > myserver.45321: UDP, length 165
14:52:48.107600 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.108342 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.109062 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.109849 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.110590 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.111357 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.113785 IP myclient.49820 > myserver.45321: UDP, length 461
14:52:48.114968 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.115710 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.116821 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.117514 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.117955 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.119438 IP myclient.49820 > myserver.45321: UDP, length 229
14:52:48.120407 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.122927 IP myclient.49820 > myserver.45321: UDP, length 477
14:52:48.123687 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.126193 IP myclient.49820 > myserver.45321: UDP, length 493
14:52:48.128326 IP myclient.49820 > myserver.45321: UDP, length 445
14:52:48.130825 IP myclient.49820 > myserver.45321: UDP, length 485
14:52:48.132055 IP myclient.49820 > myserver.45321: UDP, length 165
14:52:48.133006 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.133721 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.134511 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.135206 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.136272 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.136875 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.137939 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.138730 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.141217 IP myclient.49820 > myserver.45321: UDP, length 493
14:52:48.142165 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.143114 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.143551 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.144576 IP myclient.49820 > myserver.45321: UDP, length 109
14:52:48.147124 IP myclient.49820 > myserver.45321: UDP, length 485
14:52:48.148139 IP myclient.49820 > myserver.45321: UDP, length 133
14:52:48.150761 IP myclient.49820 > myserver.45321: UDP, length 477
14:52:48.152777 IP myclient.49820 > myserver.45321: UDP, length 461
14:52:48.153682 IP myclient.49820 > myserver.45321: UDP, length 93
14:52:48.154376 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.155402 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.155894 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.156865 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.157860 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.158393 IP myclient.49820 > myserver.45321: UDP, length 117
14:52:48.160437 IP myclient.49820 > myserver.45321: UDP, length 445
14:52:48.163377 IP myclient.49820 > myserver.45321: UDP, length 477

```

My assumption is that one outputs UDP vs NTPvX matters?

---

### Post by The Cog on 2012-09-05
I suspect that something odd is happening at the client end. In the working connection, the client only ever use a single UDP port. 

In the UDP123 connection, the client appears to change port, switching to port 123 itself. Also, you can see the 42-byte packet retrying at 2, 4, 8 second retry intervals. This is typical of a connection attempt where there is no reply.

I think this might prove hard to debug, but I suspect that something is interfering with the communications between the two ends. Maybe NAT somewhere along the path?

---

### Post by saltydk on 2012-09-05
You don't think it has to do with the "NTPv7, unspecified, length 42" reply the server gives?

I have a subscription to StrongVPN where I use UDP 123 without any issues so I know that it is possible on the client side.

I saw a post somewhere where they did a port reroute to get around NTP interfering (although I have uninstalled the daemon). IE: Server runs on UDP 1194 but since client is only able to use UDP 123 you reroute 123 traffic to 1194 on the server. Would this get around the wierd NTP "protocol" shown in my UDP 123 connection attempt above?

---

### Post by The Cog on 2012-09-05
> **saltydk said:**
> You don't think it has to do with the "NTPv7, unspecified, length 42" reply the server gives?
No. That's just tcpdump thinking that since it's port 123 then it must be NTP, and trying to decode the packet as such as it prints it for you. You should ignore the decode info - all you can use is the address, port, packet size.
> 
I have a subscription to StrongVPN where I use UDP 123 without any issues so I know that it is possible on the client side.
I know that UDP is not so easy as TCP to perform NAT on. It could be that the old StrongVPN session is still occupying the NAT entry in the router - it may be worth waiting overnight and then trying the openvpn in the morning when all the other NAT sessions should have timed out.

---

### Post by saltydk on 2012-09-05
I have other computers that have not used another vpn client, ever. So doubt its strongvpn related.

Thanks for the help but I have a hard time seeing what could be causing this.

---

### Post by The Cog on 2012-09-06
It bothers me that when you use port 123, it appears that the client is sending packets on port 123. On the higher port numnber, the client sticks to a single port.

My next step would be to run wireshark or tcpdump on the client to verify what is really happening there. Try to marry up what one end sees with what the other end sees. I still think there is some unexpected interference going on in the network between the two machines.

---

### Post by saltydk on 2012-09-06
> **The Cog said:**
> It bothers me that when you use port 123, it appears that the client is sending packets on port 123. On the higher port numnber, the client sticks to a single port.

My next step would be to run wireshark or tcpdump on the client to verify what is really happening there. Try to marry up what one end sees with what the other end sees. I still think there is some unexpected interference going on in the network between the two machines.

When I try to connect wireshark reports the following:
myclient -> myserver ---- NTP ---- NTP Reserved (Malformed Packet)
myserver -> myclient ---- ICMP --- Destination Unreachable (Port Unreachable)

---

### Post by saltydk on 2012-09-06
I remembered that I had only used my laptop for strongvpn udp 123 at school and then retested that connection from my home connection. I am unable to connect to strongvpn from either PC at home so will test my settings from school tomorrow. I suppose either my router or ISP is somehow changing stuff sent out on port UDP 123.

---

### Post by The Cog on 2012-09-06
Is that on the client or the server?

It occurs to me that the tcpdump command I gave you was only looking for UDP port 123 - it would not have shown ICMP unreachables. Perhaps you should just run **sudo tcpdump -n** and see if your server is sending ICMP port unreachable messages - it shouldn't be because your netstat output shows the port being open.

---

### Post by saltydk on 2012-09-06
> **The Cog said:**
> Is that on the client or the server?

It occurs to me that the tcpdump command I gave you was only looking for UDP port 123 - it would not have shown ICMP unreachables. Perhaps you should just run **sudo tcpdump -n** and see if your server is sending ICMP port unreachable messages - it shouldn't be because your netstat output shows the port being open.
Those results were from the server using wireshark. Client showed something similar but will test the same stuff from my school connection tomorrow, suspecting that its either router or ISP related.

---

### Post by saltydk on 2012-09-07
Connection could not be made from school either, while the strongvpn connection still works my own server does not seem to give any reply back. Now I am truly out of ideas.

---

### Post by saltydk on 2012-09-07
Fiddled around a bit on the linux box and suddenly it started working. I assume remnants of the NTP service must have been hidden somewhere. Thanks for the help!

---

### Post by The Cog on 2012-09-07
That's strange but good news. I was running out of ideas too.

You can mark the thread solved using the **Thread Tools** pull-down menu at the top.

---

