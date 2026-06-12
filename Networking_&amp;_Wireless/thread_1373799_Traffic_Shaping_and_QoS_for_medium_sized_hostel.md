---
title: "Traffic Shaping and QoS for medium sized hostel"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by hamena314 on 2010-01-06
Hi,

I maintain a network in a hostel for university students. 
As we often have a relatively slow connection I tried to find a solution.
A friend of mine used traffic shaping / QoS here before I got the job. But we seem to have not made the best rules for the shaping as the connection was way faster without the shaper than with.

As he himself installed the system alone I have nearly no knowledge how to put up another, better system. Any idea is welcome. :)

About the hostel:
- 90 people in this house
- 10 mbit SDSL dedicated line, full flatrate
- very mixed type of internet traffic (P2P, HTTP, EMails, Rapidshare, Torrents, Skype, ...)

I would like to install a linux router with traffic shaping, QoS and maybe even SQUID. 
Googling for the words brought so much older stuff, but nothing newer.

Who can help me, give advice and/or point to usefull resources to read? :)

HAVE PHUN!

---

### Post by puppywhacker on 2010-01-06
The best guide I know for traffic shaping is this one for Gentoo, the principles hold. (but skip chapter 2, it is not needed)

[http://forums.gentoo.org/viewtopic-t-225863-highlight-bandwidth.html](http://forums.gentoo.org/viewtopic-t-225863-highlight-bandwidth.html)

The thing with traffic shaping in IP networks is that you can only really control the uploading side. There are tricks to slow down the incoming side, but you have to accept that you basically can't control your provider. The second thing is that traffic shaping is about traffic prioritization. If your traffic demand is bigger than the link, you will always have queueing traffic. The counter intuative part is that if you limit your upload to something slightly slower than the max-upload the queueing is happening on your router and not on the DSL modem. This is how you can prioritize traffic, by holding back the queue-ing to a place you can decide what to prioritize on.

And that is what you have to do. Decide what upload has priority.

I have chopped up my traffic into three priority classes 10,20 and 30 and the parent gets 832kbit/s (bit lower than my measured upload speed) Then I chopped it into 3 overlapping speed classes and I let iptables classify what traffic to prioritize. TCP network connection setups go first, SSH is prioritized after. Then rate IPv6 traffic and local traffic high, all other traffic flies 3rd class. I must admit that I haven't the perfect setup either but at least my SSH connects a lot faster than without the rules.

```
tc qdisc add dev eth1 root handle 1: htb default 30
tc class add dev eth1 parent 1: classid 1:1 htb rate 832kbit
tc class add dev eth1 parent 1:1 classid 1:10 htb rate 500kbit ceil 832kbit prio 0
tc class add dev eth1 parent 1:1 classid 1:20 htb rate 500kbit ceil 832kbit prio 1
tc class add dev eth1 parent 1:1 classid 1:30 htb rate 200kbit ceil 832kbit prio 2

iptables -t mangle -A OUTPUT -o eth1 -p tcp --syn -m length --length 40:68 -j CLASSIFY --set-class 1:10
iptables -t mangle -A OUTPUT -o eth1 -p tcp --tcp-flags ALL SYN,ACK -m length --length 40:68  -j CLASSIFY --set-class 1:10
iptables -t mangle -A OUTPUT -o eth1 -p tcp --tcp-flags ALL ACK -m length --length 40:100  -j CLASSIFY --set-class 1:10
iptables -t mangle -A OUTPUT -o eth1 -p tcp --tcp-flags ALL RST -j CLASSIFY --set-class 1:10
iptables -t mangle -A OUTPUT -o eth1 -p tcp --tcp-flags ALL ACK,RST -j CLASSIFY --set-class 1:10
iptables -t mangle -A OUTPUT -o eth1 -p tcp --tcp-flags ALL ACK,FIN -j CLASSIFY  --set-class 1:10
ip6tables -t mangle -A OUTPUT -o eth1 -j CLASSIFY --set-class 1:10
iptables -t mangle -A OUTPUT -o eth1 -d 192.168.1.0/24 -j CLASSIFY --set-class 1:20
iptables -t mangle -A OUTPUT -o eth1 -p tcp --dport 22 -j CLASSIFY --set-class 1:20
iptables -t mangle -A OUTPUT -o eth1 -p tcp --sport 22 -j CLASSIFY --set-class 1:20

```

In addition (or alternative) you can use squid's delay pool which slows down the incoming side so that the ACK's are not sent to quickly, as the biggest problem is clogging the line, so slowing down the stream is actually improving the responsiveness. small pages load quicker, large downloads are moderated. Plus the caching lowers the repetitive network traffic. I don't know how to configure squid, but also the old info is bound to be valid.

---

### Post by puppywhacker on 2010-01-06
And when I come to think about it, I probably should prioritize ACK packets to use the TCP window size to fill quicker. letting the othersize send packets slower.

---

