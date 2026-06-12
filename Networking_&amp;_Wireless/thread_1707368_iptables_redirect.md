---
title: "iptables redirect"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by viperce on 2011-03-15
Hi,

I wonder if someone can help me with this, i need to forward port 80 on my ubuntu server to another machine on my network

my incoming connection is ppp0 & my network machine is 192.168.2.250 (eth0)

Thanks for the help

---

### Post by viperce on 2011-03-16
Bump

---

### Post by BkkBonanza on 2011-03-16
Try,

iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to 192.168.2.150

You will likely have to enable forwarding,

echo 1 > /proc/sys/net/ipv4/ip_forward

These both need to be done after booting so should be added to a script in /etc/network/if-up.d/ directory where they get run at init.

---

### Post by HermanAB on 2011-03-16
Howdy,

You can also use socat.

---

### Post by viperce on 2011-03-16
hi Bonanza 

I tried the commands you gave me but they did not seem to work.
any other ideas?

---

### Post by BkkBonanza on 2011-03-16
That command should work. I've used the same on my Ubuntu based router. Can you post the output of **iptables -vnL** here? Note, you will need to use sudo when you do anything with iptables.

Also the output of the **route -n** command because if you don't have a route set correctly then it won't go where you expect. Is there a second interface for your LAN other than ppp0? eg. eth0

---

### Post by viperce on 2011-03-16
iptables -vnL
> Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  873  217K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 460K   98M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 1759 87024 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp multiport dports 25,3128 
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:10000 
  632 30320 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp multiport dports 25,3128 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp multiport dports 80,5900 
    1    52 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5900 
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp multiport dports 21,22 
    0     0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp multiport dports 21,22 
    1    40 DROP       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1025:65535 flags:0x17/0x02 
   42  5496 DROP       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpts:1025:65535 
   57 18931 DROP       udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp dpts:1025:65535 
   45  8688 DROP       udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp dpts:1025:65535 
    3   144 DROP       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1:1024 
    0     0 DROP       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1:1024 
    0     0 DROP       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1:1024 
    0     0 DROP       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpts:1:1024 
 1319  180K DROP       udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp dpts:1:1024 
 3328  420K DROP       udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp dpts:1:1024 
    7  1292 DROP       all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
   57  1824 DROP       all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
  121  3872 DROP       all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 798K packets, 1020M bytes)
 pkts bytes target     prot opt in     out     source               destination

route -n
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
41.133.132.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.3.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


ye i have eth1

---

### Post by BkkBonanza on 2011-03-16
I should have also asked for **iptables -t nat -vnL** since that isn't shown in your listing. The routing seems ok. At least something for 192.168.2.150 should be going out eth0, which I assume is the correct network for the destination server.

Also note that you have a DROP on eth0 for inputs to destination port 1-1024. I'd expect that isn't causing the issue but for the purposes of debugging I'd say it's best to test with a clean iptables to be sure there isn't some interefence from other rules.

---

### Post by viperce on 2011-03-16
iptables -t nat -vnL 
> Chain PREROUTING (policy ACCEPT 32218 packets, 2867K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    4   192 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150 
  798 38304 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150 
Chain OUTPUT (policy ACCEPT 3533 packets, 226K bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain POSTROUTING (policy ACCEPT 3533 packets, 226K bytes)
 pkts bytes target     prot opt in     out     source               destination   
 
ty i will try that so long

---

### Post by viperce on 2011-03-17
Morning,
 OK I removed all the rules & started again but it still will not work.
I can connect to the web server locally no problem [http://192.168.2.150](http://192.168.2.150)
but still no joy through the ppp0 connection :(

Here is everything you asked me for yesterday thanks again for the help

iptables -vnL
> 
Chain INPUT (policy ACCEPT 2198 packets, 204K bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 3 packets, 152 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 725 packets, 94037 bytes)
 pkts bytes target     prot opt in     out     source               destination 
iptables -t nat -vnL
> 
Chain PREROUTING (policy ACCEPT 847 packets, 102K bytes)
 pkts bytes target     prot opt in     out     source               destination 
    4   204 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150

Chain POSTROUTING (policy ACCEPT 12 packets, 783 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 11 packets, 731 bytes)
 pkts bytes target     prot opt in     out     source               destination 
route -n
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
41.133.132.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.3.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


also checked ip_forward
> root@proxyserver:/# cat /proc/sys/net/ipv4/ip_forward
1


---

### Post by viperce on 2011-03-17
Just as a test I did this

>  iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 504 packets, 62767 bytes)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150
    1    52 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150
    0     0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150

Chain POSTROUTING (policy ACCEPT 1 packets, 52 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

then i tried to connect to [http://192.168.2.154](http://192.168.2.154) which should have routed me to 192.168.2.150
but is did not work either :(

---

### Post by BkkBonanza on 2011-03-17
Looking at this again, if you are trying to connect from the machine that these rules are on, to some other machine, then you would need to put them in POSTROUTING instead of PREROUTING. 

Here's my handy dandy [diagram]("http://postimage.org/image/350n5z37o/") of how the iptables flow works...

PREROUTING will rewrite addresses for the interface specified coming into the machine and POSTROUTING will rewrite for packets on the way out. The routing table should direct to the correct interface based on IP address.

---

### Post by BkkBonanza on 2011-03-17
I just reviewed my own iptables rules on my router and one thing I noticed is that I have SNAT in the POSTROUTING chain to handle stuff going out to the net getting back to the local machine. 

It occurred to me that without a similar rule your requests may get to the server port 80 but not make it back to the originating machine without a reverse rule. (If your server log shows requests but they don't get back to the original browser... they may get dropped when coming back via the router).

eg. if you want requests coming in on ppp0 to return correctly out ppp0 you may need

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

or (but not both)

iptables -t nat -A POSTROUTING -o ppp0 -j SNAT --to WANIP
(where WANIP is the IP address of the ppp0 interface)

I didn't notice this before because I'd not thought of the normal masquerading that my router does even when port forwarding isn't being used.

---

### Post by viperce on 2011-03-17
I tried to settings earlier again with no luck, so i started tracing the problem & found that the virtual machine which is connected to the net is unable to ping the 192.168.2.150 web server O_o
not sure why.

The web server is able to ping the proxy server though.

---

### Post by SeijiSensei on 2011-03-17
Use traceroute to see where the connection dies.

Often problems like this arise because routing is incorrectly configured on one end of the connection or the other.  You should also check to make sure that IP forwarding is enabled in the kernel on all machines in the chain that have multiple interfaces.  (If 'cat /proc/sys/net/ipv4/ip_forward' returns zero, forwarding is disabled.  Read the comments in /etc/sysctl.conf to find out how to fix this.)

---

### Post by viperce on 2011-03-18
i re-installed the machine I am forwarding from again
first thing i did was setup & check network to make sure it worked i can ping server everything works fine now.

then i created the ppp0 connection, echo 1 > /proc/sys/net/ipv4/ip_forward, iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to 192.168.2.150 and iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

tested & its not working :'(

I removed iptables completely from the web server just in case but still no joy.

> root@route:/home/administrator# iptables -vnL
Chain INPUT (policy ACCEPT 691 packets, 76184 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 3 packets, 152 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 201 packets, 49745 bytes)
 pkts bytes target     prot opt in     out     source               destination > root@route:/home/administrator# iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 1406 packets, 136K bytes)
 pkts bytes target     prot opt in     out     source               destination 
    1    52 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.2.150

Chain POSTROUTING (policy ACCEPT 1 packets, 52 bytes)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 MASQUERADE  all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0  

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination > root@route:/home/administrator# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
41.133.132.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.2.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
root@route:/home/administrator#
> root@route:/home/administrator# cat /proc/sys/net/ipv4/ip_forward
1
root@route:/home/administrator#
what could i be doing wrong??

---

### Post by BkkBonanza on 2011-03-18
Does the access log on the webserver show any hits from you? I'm curious if the request is getting there from the redirect. That output of the nat table shows 1406 packets accepted thru the redirect rule which means something was going thru there.

They should appear in the log as though coming from the redirect machine (due to the masquerading the src IP gets changed). On the way back in theory it should get it's origin IP set back again.

I also have the following two rules in my routing script, so maybe they are needed too.

sudo iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT

but I thought the forwarding happens even without the rules and these just ensure it's replies only allowed in. But since it's not working it's worth testing these two. The --state condition is only needed to prevent non-reply traffic. ie. the first rule could be just like the second rule.

---

### Post by viperce on 2011-03-18
i found if i do echo 1 > /proc/sys/net/ipv4/ip_forward, iptables -t nat -A PREROUTING  -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.2.150 and iptables -t  nat -A POSTROUTING -o eth0 -j MASQUERADE

then connect to [http://192.168.2.153](http://192.168.2.153) (new forwarding pc ip) it routes me to the webserver but if i change it to ppp0 it does not work :(

---

### Post by BkkBonanza on 2011-03-18
If you're doing that within your own network then it would make sense. I'm not sure just what the network layout is there. I'd assumed you had outside requests coming via ppp0 that you wanted to go to the web server. That's why the suggested rule grabs packets on ppp0. But yes, if you are within the network (connected to eth0) and send a request it wouldn't be coming into the redirect machine on ppp0 but on eth0. 

If you change the rule to not have -i (interface) option at all then it should redirect any traffic regardless of where it comes from, based on only the dest port being 80. I guess it depends what you intend.

---

### Post by viperce on 2011-03-22
i tried to
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 192.168.2.150
iptables -t   nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t   nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT

and it still does not work on ppp0 works fine on the local LAN but not externally :(

---

### Post by viperce on 2011-03-22
should i use ppp0 or dsl-provider or are they the same thing?

---

### Post by BkkBonanza on 2011-03-22
You should use whatever interface name is listed in output of **ifconfig** command.

I suggest using traceroute to see what route your packets take from your request via ppp0 to the server. Also, I never heard back if the requests show up in the server log when from ppp0. This is kind of important as it narrows down if the forward or reverse route is the problem.

I'm afraid there are just so many factors at play here that I don't have access to. eg. what is the routing on the web server? If it is routing to the wrong place then return packets won't come back to your redirect machine and get lost.

---

### Post by viperce on 2011-03-22
ok what I just figured out is this, if I default apache2 to use /var/www it works page pops up & the forwarding works but if i set it up to use the moodle website it stops working....

---

### Post by viperce on 2011-03-30
I abandoned this and just put my web server directly onto the net...thanks for trying though but linux seems to be a mission to get port forwarding working.

---

### Post by viperce on 2011-04-01
After a lot more Google searches I managed to find a the solution to my problem, Just thought i would share this with you...

Got the settings from [http://ubuntu.serversignature.com/?m=201006](http://ubuntu.serversignature.com/?m=201006)

 iptables -A INPUT -m state --state NEW -i ppp0 -j ACCEPT
iptables -A FORWARD -i ppp0 -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 192.168.2.150:80
  iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT
iptables -A FORWARD -i eth0 -o ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT
  iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
  iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
  echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 >/proc/sys/net/ipv4/tcp_syncookies
echo 1 >/proc/sys/net/ipv4/conf/all/rp_filter
   
Thanks again for all the help

---

### Post by viperce on 2011-04-01
[B]how do i mark this as [Solved] now??
[/B]

---

