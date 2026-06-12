---
title: "How do you easily throttle bandwidth?"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by mag1 on 2010-11-29
I've searched but all i find are threads from ancient history that involve installing or messing around with terminal, im looking for an easy to use app with a gui that lets me simply type in the upload and download speed or is that asking too much? ;)

---

### Post by sedawk on 2010-11-29
There are different ways to achieve this.
It depends on what the traffic looks like and
the structure on the network, e.g. if you have
a bottleneck like a DSL-connection many people use.

* one way of completely slowing down a computers network
  card (eth0, eth1, ...) is to reduce the speed of the
  network card from Gigabit to 100 Mbit, or from 100 Mbit
  to 10 Mbit. (one tool to do this is ethtool).

* many applications have a feature to limit the speed,
  e.g rsync has the --bwlimit=_limit_ parameter. That is
  much better than slowing down the full network.

* If we are talking about web access you might try to
  use a web proxy that has some features to limit
  the bandwidth for certain clients. (squid?)

* if you want to have better control check for
  "linux traffic shaping". 
  [ One tool needed is "tc" and a kernel that
    has support for CONFIG_NET_SCH_HTB and 
    CONFIG_NET_SCH_DSMARK ].

---

### Post by Kernelingus on 2010-11-29
Judging from the response you've gotten, it appears you may be.  :)

IMHO, you'll not likely become a proficient user of anything Linux-based (like Ubuntu) if you're averse to "messing around with terminal."  Executing commands from the command line is part of the experience.

As for your bandwidth throttling issue, which program's use of your bandwidth are you trying to throttle?  Most (if not all) p2p file-sharing programs let you adjust this, if that's what you're trying to do.  (For instance, if you're using Transmission for bitTorrent services, try "Edit > Preferences > Speed.")  

If you're talking about *all* the bandwidth on your whole LAN, your router probably gives you some means of adjusting this as well.  Just log into it through its http interface.  If you need to find out its address, do an ifconfig.  (Warning, however: you'll have to "mess with terminal.")

Good luck.  :)

---

### Post by mag1 on 2010-11-30
See this is the problem, i wasn't really helped with what i asked but don't get me wrong i appreciate you trying, i actually do know how to use the command line somewhat as i've had no choice, i've used ubuntu for years but what bugs me is the over dependence on it to do some really simple stuff that could easily have a gui to get quick results, but no we still need to do things the awkward way and read pages of text to understand how to do something simple.

I just want to throttle the lan connection not individual programs otherwise i would of asked, i know some like p2p have that capability, though it is mainly for the browser i've looked and firefox doesn't have a plugin for it anymore, if there is a simple command i can use to change the download rate to 350Kb/s i would be happy, it would probably help me and others in the future if someone could just show us how?

---

### Post by Boondoklife on 2010-11-30
While a router would serve the best solution as it is a central junction, check out [this]("http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html") it seems interesting and like what you are trying to achieve.

---

### Post by mag1 on 2010-11-30
Thanks, i was hoping i wouldn't have to use commands but trickle does look useful so i will give that one a go, maybe one day linux will have a gui for everything?

---

### Post by puppywhacker on 2010-11-30
What you are asking for is "Traffic Shaping" documented in the advanced  networking howto. Advanced, so this is not simple GUI stuff.

[http://tldp.org/HOWTO/Adv-Routing-HOWTO/]("http://tldp.org/HOWTO/Adv-Routing-HOWTO/")

The principle is that the kernel keeps queues and assigns bandwidth based on the rules for these queues.

A way to control the download link is to drop or delay ACK packets, so that the send window on the sending side will fill and they will send info slower.

The below example is what I would use to control the UPLOAD streams. download speeds can't be controlled, because it is the sender (your provider) that has the control.

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

---

### Post by mag1 on 2010-11-30
Everything that can reasonably have a gui should have a gui, it's nearly 2011 and linux has had plenty of time to mature yet still many silly little things can't be done with a gui even though it would make life easier for everyone, that said i appreciate the help and will use the cmd line if its simple enough, though i just found out trickle doesn't work with firefox and theres no known fix or update in sight...

---

### Post by tridentblack on 2011-09-27
I agree this should be more easily doable. I'm trying to download something with my browser. My Girlfriend is watching Netflix. Her movie is breaking up because my computer is hogging bandwidth. If I could cut my bandwidth by 1/3, she could watch movie and I could have my thing in 30 minutes. Otherwise I have to wait for her to stop watching movies, or I have to stop her movie for 10 minutes. This type of thing happens all the time, and its something that should just be there...In the browser, or in Ubuntu, not in some complex process. 

Actually, it should be handled at the network level. The AppleTV should broadcast the bandwidth it needs with a priority number, and my downloads should not, and the router should figure it out. But until then, a fix is in order.

---

