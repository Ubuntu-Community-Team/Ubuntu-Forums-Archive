---
title: "redirect routing on non-default interface"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by docawk on 2008-12-11
I have a linux running firewall/router machine, connecting LAN to the internet with two interfaces (no load balancing or other connections). One is a fast connection with dynamic IP (ADSL) which is the default route, the other is a static IP (T3) connection (used for mail sever and other services available from www).
Additional I want to provide our intranet (located in the LAN) access to workes outside the office, using a port on the static firewall IP, which will be redirected (dnat) by iptables prerouting rule and allowed forwarding to LAN intranet sever port.
The scenario is woking when the T3 connection is default gateway in the main routing table. It is not working when I switch the default gateway to the ADSL connection.
The incoming packets are trackable with tcpdump and dnat redirect in the prerouting table is working (notification in syslog by iptables). Missing are the packets on the interface to LAN and the forwarding notification by iptables is also missing. So I think this is a routing problem.

I hope someone can help, or getting me clues what to check.

Thank you,

Oliver




Here is some information on the network topology and snips from the routing/firewall script:
```

                                  /-------------------\
                                  |       DMZ         |
                                  |  static IP        |
                                  \-------------------/
                                         |
                                       2 |
                                  /--------------------------------\
                    StaticIP      | Static IP                      |
                  /----------\  1 |                                | 0  /-----------------\
                  |    T3    | -- |       Firewall/Router          | -- |   LAN           |
                / \----------/    |                                |    |                 |
               /                  |                                |    \-----------------/
/-------\     /                   \--------------------------------/ 
|  WWW  | ---<                           |                           
\-------/     \                        3 |                           
               \                         |                           
                \ /----------\           |         
                  |   ADSL   | ---------/                 
                  \----------/                    
                    DynamicIP                              
                                                                     
                                                                     


function SetIPROUTEmain () {
   
    ExitStatus=0
    echo -en " - Setting Routing table main " >>$MessageDev
    $IP route add $LAN_IP_RANGE dev $LAN_IFACE src $LAN_IP
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $ADSL_IP_RANGE dev $ADSL_IFACE src $ADSL_IP
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $DMZ_IP_RANGE dev $DMZ_IFACE src $DMZ_IP
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $T3_GATEWAY dev $T3_IFACE src $T3_IP
    ExitStatus=$(($ExitStatus+$?))

    $IP route add default via $ADSL_GATEWAY dev $ADSL_IFACE
    ExitStatus=$(($ExitStatus+$?))

    $IP route flush cache
    ExitStatus=$(($ExitStatus+$?))
    PRINT_EXIT_STATUS $ExitStatus
    echo >>$MessageDev
}
function SetIPROUTEadsl () {
   
    ExitStatus=0
    echo -en " - Setting Routing table ADSL " >>$MessageDev

    $IP route add $ADSL_IP_RANGE dev $ADSL_IFACE src $ADSL_IP table ADSL
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $T3_GATEWAY dev $T3_IFACE src $T3_IP table ADSL
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $DMZ_IP_RANGE dev $DMZ_IFACE src $DMZ_IP table ADSL
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $LAN_IP_RANGE dev $LAN_IFACE src $LAN_IP table ADSL
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $LO_IP_RANGE dev $LO_IFACE src $LO_IP table ADSL
    ExitStatus=$(($ExitStatus+$?))
    $IP route add default via $ADSL_GATEWAY dev $ADSL_IFACE table ADSL
    ExitStatus=$(($ExitStatus+$?))

    $IP rule add from $ADSL_IP table ADSL
    ExitStatus=$(($ExitStatus+$?))

    $IP route flush cache
    ExitStatus=$(($ExitStatus+$?))
    PRINT_EXIT_STATUS $ExitStatus
    echo >>$MessageDev
   
}   
function SetIPROUTEt3 () {
   
    ExitStatus=0
    echo -en " - Setting Routing table T3 " >>$MessageDev

    $IP route add $ADSL_IP_RANGE dev $ADSL_IFACE src $ADSL_IP table T3
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $T3_GATEWAY dev $T3_IFACE src $T3_IP table T3
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $DMZ_IP_RANGE dev $DMZ_IFACE src $DMZ_IP table T3
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $LAN_IP_RANGE dev $LAN_IFACE src $LAN_IP table T3
    ExitStatus=$(($ExitStatus+$?))
    $IP route add $LO_IP_RANGE dev $LO_IFACE src $LO_IP table T3
    ExitStatus=$(($ExitStatus+$?))
    $IP route add default via $T3_GATEWAY dev $T3_IFACE table T3
    ExitStatus=$(($ExitStatus+$?))

    $IP rule add from $T3_IP table T3
    ExitStatus=$(($ExitStatus+$?))
    $IP rule add from $DMZ_IP_RANGE table T3
    ExitStatus=$(($ExitStatus+$?))
 
    $IP route flush cache
    ExitStatus=$(($ExitStatus+$?))
    PRINT_EXIT_STATUS $ExitStatus
    echo >>$MessageDev
   
}   



function IPT_Intranet () {

    #-------------------------------------------------------------------------------
    # Pierce Port 20080 to Intranet WWW
    if [ "$Enable_INTRANET" = "y" ] ; then
   
        ExitStatus=0
        echo -ne " - Establish INTRANET rules " >>$MessageDev

        $IPTABLES -t nat -A PREROUTING -p TCP -i $T3_IFACE --dport 20080 -j LOG --log-prefix "DNAT 20080:"
        ExitStatus=$(($ExitStatus+$?))
        $IPTABLES -t nat -A PREROUTING -p TCP -i $T3_IFACE -d $DMZ2_IP --dport 20080 -j DNAT --to-destination $WWW_SERVER_IP:81
        ExitStatus=$(($ExitStatus+$?))
   
        $IPTABLES -A FORWARD -p TCP  -d $WWW_SERVER_IP -j LOG --log-level DEBUG --log-prefix "IPT FORWARD INTRANET:"
        ExitStatus=$(($ExitStatus+$?))
        $IPTABLES -A FORWARD -p TCP -i $T3_IFACE -d $WWW_SERVER_IP -o $LAN_IFACE --dport 81 -j ACCEPT
        ExitStatus=$(($ExitStatus+$?))

        PRINT_EXIT_STATUS $ExitStatus
        echo >>$MessageDev
   
    fi

}

```

---

### Post by jmoorse on 2008-12-12
It is my guess that you need to set iptables to route based on its state table.

What is most likely happening is routing is performed without examining said table, thus return traffic is being dropped by client machines as it is originating from the ADSL interface instead of the DS3.

I would verify this by running protocol analysis on the client machines and look for return traffic from the ADSL interface.

Given this assumption proves to be true, I would consult iptables documentation on the best way to assure stateful routing decisions.

---

### Post by docawk on 2008-12-16
I think there is a difference between stateful filtering (which iptables does) and stateful routing (which ip route does?).
From the viewpoint of the firewall filtering the packets are allowed to pass on the given route (verified through setting T3 the default route). 
Packets entering T3 interface are redirected to a certain IP:port. This still works (as logging from iptables shows). But the routing of those DNAT packages to the LAN interface fails if default route is not set to T3.
I thought I had implemented a stateful routing by adding ip rules to the main routing table, setting route tables T3 and ADSL whith respective default routes for incoming traffic from the respective interface.
.. or did I get anything wrong?

```

firewall:~# ip route list
XXX.XXX.250.185 dev eth1  scope link  src XXX.XXX.250.186
XXX.XXX.250.184/29 dev eth2  scope link  src XXX.XXX.250.186
192.168.11.0/24 dev eth3  scope link  src 192.168.11.9
192.168.10.0/24 dev eth0  scope link  src 192.168.10.9
default via 192.168.11.92 dev eth3

firewall:~# ip route list table ADSL
XXX.XXX.250.185 dev eth1  scope link  src XXX.XXX.250.186
XXX.XXX.250.184/29 dev eth2  scope link  src XXX.XXX.250.186
192.168.11.0/24 dev eth3  scope link  src 192.168.11.9
192.168.10.0/24 dev eth0  scope link  src 192.168.10.9
127.0.0.0/8 dev lo  scope link  src 127.0.0.1
default via 192.168.11.92 dev eth3

firewall:~# ip route list table T3
XXX.XXX.250.185 dev eth1  scope link  src XXX.XXX.250.186
XXX.XXX.250.184/29 dev eth2  scope link  src XXX.XXX.250.186
192.168.11.0/24 dev eth3  scope link  src 192.168.11.9
192.168.10.0/24 dev eth0  scope link  src 192.168.10.9
127.0.0.0/8 dev lo  scope link  src 127.0.0.1
default via XXX.XXX.250.185 dev eth1

```

---

### Post by mpokrywka on 2008-12-21
You can make routing stateful using stateful filtering + connection marking. Routing can be configured to use packet mark as routing key.

That said, I think you should use something like:
```
ip rule iif $T3_IFACE table T3
```
instead of "from $T3_IP table T3", because routing decision is made after PREROUTING and before FORWARD, POSTROUTING (like chain names says).

I think you should use interface matching in your routing rules to make them more clear.

If you really need "stateful" routing, I can write something.
But if your "intranet" can be selected by IP this should not be necessary.

---

### Post by docawk on 2008-12-22
I tried with your suggested modified ip rule (you are right it is more clear to use rule based on the interface rather than on the IP address). But unfortunately the results are the same.

Could you provide me a hint or link to "stateful" routing?

Another idea: What about linking both interfaces, T3 and ADSL, for load balancing. Since with my understanding this is done on a lower level, the default route is set on the bond interface, thus could solve the problem? I am not sure? Anybody an idea?

---

### Post by mpokrywka on 2008-12-22
Could you list your routing rules (**ip rule list**) so that picture would be more clear?
(to be honest, I didn't try to reconstruct your rules from your script)
If you substitute IP addresses/networks with symbols (DMZ_IP_RANGE) it would be very helpful.

About "stateful" routing:
Let's assume that your default route is ADSL_IP.
All packets destined to internet coming from LAN are forwarded to ADSL because of default route.
Now, there comes new connection on T3 from internet.
You have DNAT rule to redirect it to LAN.
Ok, routing should work - src==internet, dst==LAN -> go through LAN interface.
But host from LAN now replies and we have problem, because reply will return through default route as above.
Solution is: when DNATing also mark this connection as CAME_FROM_T3.
Now for all packets from LAN: check what connection this packet belongs.
If packet belongs to connection "CAME_FROM_T3" then forward it through T3 - not through default route.

How to do it?

One thing - there is two different "marks":
connection mark - save with connection data, accessible only to iptables
packet mark - "general purpose" mark saved with each packet, accessible from iptables, routing, traffic control and (if I am not wrong) from userspace
```

CAME_FROM_T3=0x3
# all connections coming from T3 set connection mark
iptables -t mangle -A PREROUTING -i $T3_IFACE \
                                 -j CONNMARK --set-mark $CAME_FROM_T3
# packets from LAN - set packet mark to be same as connection mark
iptables -t mangle -A PREROUTING -i $LAN_IFACE \
                                 -j CONNMARK --restore-mark
# now routing decision
ip rule add iif $LAN_IFACE fwmark $CAME_FROM_T3 table T3
# routing table T3 should contain only one route
ip route add default via $T3_GATEWAY

```

---

### Post by docawk on 2008-12-22
Here are the ip rules:

```

firewall:~# ip rule list
0:      from all lookup local 
32763:  from ADSL_IP lookup ADSL 
32764:  from DMZ_IP_RANGE lookup T3 
32765:  from T3_IP lookup T3 
32766:  from all lookup main 
32767:  from all lookup default 

```

One thing concerning the ip rules interface based: As I was writing in my last post, the change to iif rule was unsuccessful, it was not totally right: there still is no route to the intranet server, but by starting the script I am locked out of the system (I administer the system remotely via ssh on T3 interface). First try (the one I posted) seemed unchanged, but ok connection wise. A cron driven fallover script restarted the running firewall version just splits of a second after the manual start of the modified rules.

To stateful routing: I will figure out how to do, but it will take some time until I will reply with the results.

One question to the routing table T3: as I remember I needed all entries (not just the default route) inside the table to successfully route all packages. I always wondered, as all routes are set in main table. Is the main table read anyways if any special rule matches? I don't think so. That would be a reason why I had to give all routes in main, T3 and ADSL tables.

Thanks so far.

---

### Post by mpokrywka on 2008-12-22
Ok, when I saw routing rules everything was made clear.
Your setup is of course correct, you need not change anything.
All routes are needed in route table T3, because communication DMZ->LAN would otherwise fail.
(As you said - when route is found earlier, mail route table is not consulted)
You can remove loopback routes because they are added by default to special table "local".

3 lines (iptables,iptables,ip rule) I written in previous post will make intranet work as you wanted - ignore this last route line.

---

### Post by docawk on 2008-12-22
I added the iptable marks and the rule.
Now the rule list looks like this

```

0:      from all lookup local 
32762:  from ADSL_IP lookup ADSL 
32763:  from DMZ_IP_RANGE lookup T3 
32764:  from T3_IP lookup T3 
32765:  from all fwmark        3 iif eth0 lookup T3 
32766:  from all lookup main 
32767:  from all lookup default 

```

I have no difficulties on connections that were running already (esp. logging in via ssh). But no redirected connection to LAN.

Is there a way to check the marks? I tried tcpdump -vv but without noticing any marks, though a log rule with iptables says packets are right before process of marking.

---

### Post by mpokrywka on 2008-12-22
Packet mark can be checked using iptables -j LOG after applying mark - at the end of log line there will be MARK=0x03.
Are you sure that packets go to LAN (DNAT rule is working)?
Routing should forward packets internet->DMZ2_IP:20080 to LAN.
Are SYN packets going on eth0 to WWW_SERVER_IP:81 ?
Maybe you try to connect to DMZ2_IP:20080 from LAN? This won't work.

---

### Post by docawk on 2009-01-21
Sorry for my late reply .. lot of other stuff to do ... 

> **mpokrywka said:**
> Packet mark can be checked using iptables -j LOG after applying mark - at the end of log line there will be MARK=0x03.
```
    CAME_FROM_T3=0x3
    # all connections coming from T3 set connection mark
    $IPTABLES -t mangle -A PREROUTING -i $T3_IFACE \
                                 -j CONNMARK --set-mark $CAME_FROM_T3
    $IPTABLES -t mangle -A PREROUTING -i $T3_IFACE -j LOG --log-prefix "Set Mark T3:"   

```

here is the listing of according ruleset:
```
firewall:~# iptables -t mangle -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
CONNMARK   0    --  0.0.0.0/0            0.0.0.0/0           CONNMARK set 0x3 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `Set Mark T3:' 
CONNMARK   0    --  0.0.0.0/0            0.0.0.0/0           CONNMARK restore 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `Restore Mark:' 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

```

gets me in the log:
```
Jan 21 20:25:28 firewall kernel: Set Mark T3:IN=eth1 OUT= MAC=00:1b:fc:c2:bc:57:00:90:d0:ab:f2:cf:08:00 SRC=XXX.XXX.164.71 DST=DMZ2_IP LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=29419 DF PROTO=TCP SPT=56969 DPT=20080 WINDOW=8192 RES=0x00 SYN URGP=0 
Jan 21 20:25:28 firewall kernel: DNAT 20080:IN=eth1 OUT= MAC=00:1b:fc:c2:bc:57:00:90:d0:ab:f2:cf:08:00 SRC=XXX.XXX.164.71 DST=DMZ2_IP LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=29419 DF PROTO=TCP SPT=56969 DPT=20080 WINDOW=8192 RES=0x00 SYN URGP=0 

```

so no mark is set?

I checked the kernel configuration and all netfilter configurations, except for CONFIG_IP_NF_QUEUE is not set, are set to yes, so compiled into the running kernel.
I am running kernel 2.6.23.14 and iptables 1.3.6


> **mpokrywka said:**
> Are you sure that packets go to LAN (DNAT rule is working)?
Routing should forward packets internet->DMZ2_IP:20080 to LAN.
Are SYN packets going on eth0 to WWW_SERVER_IP:81 ?

Packets are incoming on eth1 (T3_IFACE) and recorded by tcpdump:

```
 tcpdump -vv -n -i eth1 | grep -v .22
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes

20:53:44.299625 IP (tos 0x0, ttl 116, id 3580, offset 0, flags [DF], proto: TCP (6), length: 52) XXX.XXX.164.71.57285 > DMZ2_IP.20080: S, cksum 0xa6e4 (correct), 232969914:232969914(0) win 8192 <mss 1452,nop,wscale 2,nop,nop,sackOK>

```

And then logged by iptables (look above).
But on LAN_IFACE or other interfaces no sign of a packet is transmitted.

When I switch the default route in the main routing table to $T3_IFACE, packets are DNATed and routed to LAN and WWW_SERVER_IP:81


> **mpokrywka said:**
> Maybe you try to connect to DMZ2_IP:20080 from LAN? This won't work.

I am testing from outside the network structure and enter form the internet.

---

### Post by docawk on 2009-01-21
Thinking about what I wrote an hour ago:

The problem seems to start earlier. Packets don't even reach the LAN_IFACE. They appear incoming on T3_IFACE, get DNATed through iptables rule and then are not detected on any interface, esp. not on LAN_IFACE where I would expect them.
To make it even more confusing when I switch setup to default route T3_IFACE instead of ADSL_IFACE in the main routing table (this is really the only difference nothing else changed) the access to intranet behind the firewall works fine.

Thoughts about packet marking and ip rules based on that mark are necessary for returning traffic through non-default interface. yes. But there seems to be more as packets don't even make it through the firewall to the LAN where they could initiate a response that could be routed back.

I hope anyone has suggestions what to check on.

---

### Post by mpokrywka on 2009-01-26
You can try listening for your packet on "any" interface:
**tcpdump -n -i any src host XXX.XXX.164.71**
and you should see which interface packet leaves box after DNATting...
If packet does not appear anywhere this means that either it is dropped by your firewall rules
(this you can control by logging packet traversal in different chains)
or by routing:
1. you can try turn on logging "martians": echo 1 > /proc/sys/net/ipv4/INTERFACE/log_martians
2. you can temporary turn off rp_filter: echo 0 > /proc/sys/net/ipv4/INTERFACE/rp_filter
(maybe routing is somehow confused about networking layout and drops packets)

---

### Post by docawk on 2009-01-28
> **mpokrywka said:**
> You can try listening for your packet on "any" interface:
**tcpdump -n -i any src host XXX.XXX.164.71**
and you should see which interface packet leaves box after DNATting...

On none of the interfaces the packets appear after entering on T3_IFACE and being DNATed.

> **mpokrywka said:**
> If packet does not appear anywhere this means that either it is dropped by your firewall rules
(this you can control by logging packet traversal in different chains)

I am logging all packages before they are dropped (by default in case they are not accepted explicitly in the chain). I see none of the related DNAT packages dropped.

The test: default route T3_IFACE produces with tcpdum:
packets come in T3_IFACE, leave LAN_IFACE
logged by firewall:
mark T3
DNAT
FORWARD
restore mark
.. everything fine.


> **mpokrywka said:**
> 
or by routing:
1. you can try turn on logging "martians": echo 1 > /proc/sys/net/ipv4/INTERFACE/log_martians

```
Jan 29 01:08:11 firewall kernel: Set Mark T3:IN=eth1 OUT= MAC=00:1b:fc:c2:bc:57:00:90:d0:ab:f2:cf:08:00 SRC=XXX.XXX.82.12 DST=DMZ2_IP LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=22679 DF PROTO=TCP SPT=56258 DPT=20080 WINDOW=8192 RES=0x00 SYN URGP=0 
Jan 29 01:08:11 firewall kernel: DNAT 20080:IN=eth1 OUT= MAC=00:1b:fc:c2:bc:57:00:90:d0:ab:f2:cf:08:00 SRC=XXX.XXX.82.12 DST=DMZ2_IP LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=22679 DF PROTO=TCP SPT=56258 DPT=20080 WINDOW=8192 RES=0x00 SYN URGP=0 
Jan 29 01:08:11 firewall kernel: martian source 192.168.10.1 from XXX.XXX.82.12, on dev eth1
Jan 29 01:08:11 firewall kernel: ll header: 00:1b:fc:c2:bc:57:00:90:d0:ab:f2:cf:08:00

```
The martian source message does not appear when I switch to T3_IFACE as default gw in main routing table.

> **mpokrywka said:**
> 2. you can temporary turn off rp_filter: echo 0 > /proc/sys/net/ipv4/INTERFACE/rp_filter
(maybe routing is somehow confused about networking layout and drops packets)
Disabling the reverse path filter on T3_IFACE does the trick. Packets getting routed after DNAT :D finally

I can see packets logged entering the firewall getting DNATed and forwarded to the intranet server, backpackets mangled and marks restored and packets leaving the right interface T3_IFACE

---

### Post by docawk on 2009-01-28
To sum up:

- Mark packets through mangle in firewall
- Add a filter rule based on packet marks
- disable reverse path filter

That solved my problem


Million thanks to mpokrywka

---

