---
title: "Iptables and SNAT"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by codingfreak on 2009-10-26
Hi

I am a newbie to iptables with NAT.

```

                            linuxbox2 (192.x.y.a)
                              |
                              |
    linuxbox1(eth1)-------- Switch ----- ftpserver(INTERNET)
    (192.x.y.b)        (194.160.1.1)
```BOX1 and BOX2 are in VLAN tagging via switch. BOX1 has a special VLAN tag for Internet. BOX2 inorder to connect to a FTP server(internet) should route via BOX1 which should do POSTROUTING(SNAT) and send the packet to FTP server.

So I added the following rules in my IPTABLES

```
    $IPTABLES -t mangle -A PREROUTING -p tcp --dport 21 -s 192.x.y.a -j ACCEPT
    $IPTABLES -t mangle -A FORWARD -p tcp --dport 21 -s 192.x.y.a -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j ACCEPT
    $IPTABLES -t nat -A POSTROUTING -s 192.x.y.a -p tcp --dport 21 -j SNAT --to-source 192.x.y.b
```If I ping from BOX2 to BOX1 it is working fine. But if I try to ftp to the ftpserver then NAT table in iptables comes into picture and ftp is not successfull.

If I do the tcpdump at eth1 I do see ftp packets coming from BOX2 to BOX1 but no packets leaving from BOX1 to ftpserver.

```
    IP 192.x.y.a.45388 > 10.p.q.r.21(ftpserver): S 1380128644:1380128644(0) 
    win 5840 <mss 1460,sackOK,timestamp 16897 0,nop,wscale 2>
    IP 192.x.y.a.45388 > 10.p.q.r.21: S 1380128644:1380128644(0) 
    win 5840 <mss 1460,sackOK,timestamp 17647 0,nop,wscale 2>
    IP 192.x.y.a.45388 > 10.p.q.r.21: S 1380128644:1380128644(0) 
    win 5840 <mss 1460,sackOK,timestamp 19147 0,nop,wscale 2>
```Checking the status of the iptables I do see that a packet for nat chain. But I dont see any packets leaving to FTP server in tcpdump.

So if a packet is gone through postrouting option in nat table why hasnt it gone to ftp server ??

**NOTE: All my IPTABLE rules should be based on ip-address but not on interface as there is a chance of change in interface names but in ip-addresses.**

---

### Post by mpokrywka on 2009-10-26
> **codingfreak said:**
> Hi
Checking the status of the iptables I do see that a packet for nat chain. But I dont see any packets leaving to FTP server in tcpdump.


To be 100% sure that packet is SNAT-ted and leaves by correct interface insert logging into POSTROUTING chain:
```
$IPTABLES -t nat -I POSTROUTING -s 192.x.y.a -j LOG --log-prefix "SNAT active: "
```
then check syslog if all packet data is correct (out=, src=, dst=)

If packet got that far (iptables POSTROUTING nat), there is almost no way something would block it - only maybe traffic control could drop it. My bet is it leaves by incorrect interface (eth0? routing check needed) or does not really get to POSTROUTING nat (iptables filtering/ip_forward not enabled).

BTW, your rules would need small rework to correctly deal with FTP data connections. But first you should get FTP control connection working...

---

### Post by codingfreak on 2009-10-26
> If packet got that far (iptables POSTROUTING nat), there is almost no way something would block it - only maybe traffic control could drop it. My bet is it leaves by incorrect interface (eth0? routing check needed) I would make a check on it ..

> does not really get to POSTROUTING nat (iptables filtering/ip_forward not enabled).ip_forward is enabled. I do see a increase in counter value for packets under POSTROUTING chain in nat table. So it indicates that it has reached the postrouting chain.

> BTW, your rules would need small rework to correctly deal with FTP data connections. But first you should get FTP control connection working...you mean I should I have a ftp rule for port 20 even ??

---

### Post by mpokrywka on 2009-10-30
> **codingfreak said:**
> you mean I should I have a ftp rule for port 20 even ??

Make sure you have **nf_nat_ftp** module loaded, this nat helper take care of ftp data connections handling.
This means that ftp-data connections will have *ctstate* set to **RELATED** instead of NEW, and this way you can allow them to pass.

You listed only few iptables rules so I don't know what you accept/drop, but if linuxbox2 will try to use passive ftp, your mangle PREROUTING chain rule won't match it. You'll need to add something like:
```

$IPTABLES -t mangle -I PREROUTING -p tcp -s 192.x.y.a -m state --state RELATED -j ACCEPT

```
Same for FORWARD, and if linuxbox1 can be connected from internet, you'll probably want to add support for active ftp (connection ftp-server -> client)

---

