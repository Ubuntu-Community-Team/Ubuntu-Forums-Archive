---
title: "Multiple (isolated) NICs"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by alnilamski on 2009-02-24
Hey all,

I have a machine running Hardy, with two ethernet ports, eth0 and eth1.
eth0 goes to the router and is for general LAN/WAN stuff. Works fine.

I want eth1 to go to a little Embedded Linux machine with no interface of its own (named Viper), and I don't have much experience doing this kind of thing. I currently can access Viper only with minicom through a COM port, and Viper has an ethernet port that appears to be working (I can play with ifconfig in Viper) that I want to be able to commune with this Ubuntu computer, since the COM is slow.

So far, I've tried setting Ubuntu's eth1 to an arbitrary IP,
```
ifconfig eth1 192.168.1.1
```
where the third group (xxx.xxx.1.x) is different from eth0's, which as I understand should isolate the two NICs from each other...
...and setting Viper's eth0 to a similar one
```
ifconfig eth0 192.168.1.2
```

I don't know much about the *route* command other than basic gateway-setting-stuff. For a stab, I tried setting Viper's IP as the destination:
```
route add 192.168.1.2 dev eth1
```
on the Ubuntu machine and vice versa on Viper. I then tried telling one to ping the other, to no avail.

Again, these are only the shots in the dark of someone with only basic experience in linux networking (i.e. setting up computers to be on a regular old network through a router). It probably sounds like I'm asking "can someone teach me everything about how to network computers?" and that's a lot. I'm trying to find guides and other literature, but I'm not entirely sure where to even start.

Can someone at least point me in the right direction as to what kind of keywords to look for, to find some literature to help me with this sort of thing? Or if the solution is easier than I think, an answer would also be appreciated. ;)

---

### Post by puppywhacker on 2009-02-24
on the ubuntu machine, try to see if the ethernet link is up

```
mii-tool
```

on both machines print the route, they should both have already have a net-route to 192.168.1.0 by default, this happens when you set the interface (plus netmask)

```
netstat -nr
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1

```

if the IP level and the route is working, the viper board should show up in the arp table. ping the board, regardless if it responds or not
```
arp -a
```

your viper board or your linux might not support or block ping (or block all icmp) check the firewall on both sides.
```
iptables -L -v
```

on the ubuntu look at the "ifconfig eth1" to see if you have packets coming in (Rx) and going out (Tx)

```
ifconfig eth1
```

when nothing works, form ubuntu sniff the network with tcpdump, you should have at least something
```
tcpdump -i eth1 -vv
```

You shouldn't trust ping too much, there are quiet a few things that would break ping.

---

### Post by alnilamski on 2009-03-02
Some strange things went down when I tried your advice, though it was helpful.

mii-tool, after setting both parties' ifconfig properly, yielded:
```
sudo mii-tool
eth0: negotiated 100baseTx-FD flow-control, link ok
eth1: negotiated 100baseTx-FD, link ok

```

After going through your initial steps, at one point, pinging the board worked! I was very excited. But now for some reason, it doesn't work - even though I don't think I changed anything! Instead the Ubuntu machine says:

```
ping 192.168.2.2
PING 192.168.2.2 (192.168.2.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

[4]+  Stopped                 ping 192.168.2.2

```
*EDIT: This happens with sudo as well*

(note, I'm now working with 192.168.2.x for various reasons but the situation is still the same)

Also, the board does NOT show up on "arp -a" at first, BUT when I do the following:
```
tcpdump -i eth1 -vv
```
and then ping Ubuntu from the board, a bunch of ping attempt traffic shows up, as well as what appear to be arp exchanges:
```
 sudo tcpdump -i eth1 -vv
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
12:09:46.038036 arp who-has 192.168.2.1 tell 192.168.2.2
12:09:46.038086 arp reply 192.168.2.1 is-at 00:04:76:ec:5e:f6 (oui Unknown)
12:09:46.038220 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 104) 192.168.2.2 > 192.168.2.1: ICMP echo request, id 14595, seq 0, length 84
12:09:47.048273 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 104) 192.168.2.2 > 192.168.2.1: ICMP echo request, id 14595, seq 1, length 84
...+ a bunch more of these incoming ping attempts

```
On the board, the ping attempt returns nothing. But after that point, when I do "arp -a" on the Ubuntu machine, I get (along with the usual eth0 answers)
```
? (192.168.2.2) at 00:80:66:03:96:2A [ether] on eth1
```
which means it's being found.

Also, "iptables" does not exist on the Viper board, and yields results that I don't know how to interpret on Ubuntu. I'll start reading up on *iptables*. Since the connection is hard-wired between the board and ubuntu, would it make sense to tell eth1 to allow all traffic? How might I do that? Would that maybe fix my problem?

Thanks for your help so far.


**RE-EDIT:**
Turns out Firestarter was running! When I told Firestarter to stop the firewall, ping worked both Ubuntu -> Viper, and Viper -> Ubuntu. Now I have to figure out how to tell Firestarter to allow everything on eth1...

---

