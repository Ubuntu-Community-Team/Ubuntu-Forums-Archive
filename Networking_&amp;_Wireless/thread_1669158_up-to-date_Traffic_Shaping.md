---
title: "up-to-date Traffic Shaping"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by Runaway1956 on 2011-01-17
As others have mentioned, in other threads - traffic shaping is a somewhat troublesome subject.  A guy can google for hours, and find ancient posts, referencing kernels and tools that are no longer supported anywhere.  Many, if not most, aren't supported by Ubuntu, and never were.

Wondershaper is the single most useful tool I've found so far - but you can't always install it, or set the rules for it, on all of the network computers.

Some of us don't really have the option of installing a Linux box in-line to use as a router.  (In some case I do, in other cases, not.)

I stumbled over this link in my searches:  [http://nsd.dyndns.org/shapedsl/](http://nsd.dyndns.org/shapedsl/)

Specifically, this quote caught my attention:
[quote=ndade] "The fix is to shape the uplink's traffic before it gets into the DSL modem's upload buffer. And the tool is linux, specifically linux's IP forwarding and traffic shaping capabilities. The cleanest way to add this to your home network is to give the linux box two NIC cards, and place it between everything else and the DSL modem. However if you are a sophisticated DSL user you probably already have a router and want the linux box to be on the same network as the rest of the machines in the house. Apart from that, placing the linux box between the DSL modem and the rest of the house means the linux box must be up and running or the internet connection is down. The way I set things up is to place the traffic shaping linux box in the same network as everything else, and have it send gratuitous ARP packets claiming it is the gateway. This tricks the rest of the machines in the house into sending it their packets destined for the outside world as long as they keep receiving the GARPs. If the linux box is down, the GARPs don't come, the ARP entries time out, the hosts send ARP requests and receive a reply from the router. This way if the linux box is down the internet connection switches over automatically.

With this GARP trick, packets being sent from anywhere in the house to an outside destination take an extra hop through the linux traffic shaper, while packets between hosts in the house and packets from outside into the house go directly to their destinations. This is exactly the desired effect." [/quote]

As usual, with posts of this type, the author goes on to mention outdated kernels, as well as qdisc - which I cannot find any mention of in Synaptic.  The rest of the tools he mentions are all available, but not qdisc.



Question is - how do I modernize and/or update the script for use on a current Ubuntu box?  There is no guidance regarding proper naming, or placement of the script - or, not that I can understand. 

```



#!/bin/sh


case "$1" in
    start)
	# configure eth0 so that there is a bandwidth cap on large packets going up the DSL line
	# and then garp advertising the true gateway's IP, so that other hosts use us rather than it

	# enable ip forwarding
	echo 1 >/proc/sys/net/ipv4/ip_forward 

	# disable sending of icmp redirects (after all, we are deliberatly causing the hosts to use us instead of the true gateway)
	echo 0 >/proc/sys/net/ipv4/conf/all/send_redirects
	echo 0 >/proc/sys/net/ipv4/conf/eth0/send_redirects

	# clear whatever is attached to eth0
	# this can fail if there is nothing attached, btw, but that is fine
	/sbin/tc qdisc del dev eth0 root 2>/dev/null

	# add default 3-band priority qdisc to eth0
	/sbin/tc qdisc add dev eth0 root handle 1: prio

	# add a <128kbit rate limit (matches DSL upstream bandwidth) with a very deep buffer to the bulk band (#3)
	# 99 kbit/s == 8 1500 byte packets/sec, so a latency of 5 sec means we will buffer up to 40 of these big
	# ones before dropping. a buffer of 1600 tokens means that at any time we are ready to burst one of
	# these big ones (at the peakrate, 120kbit/s). the mtu of 1518 instead of 1514 is in case I ever start
	# using vlan tagging, because if mtu is too low (like 1500) then all traffic blocks
	/sbin/tc qdisc add dev eth0 parent 1:3 handle 13: tbf rate 99kbit buffer 1600 peakrate 120kbit mtu 1518 mpu 64 latency 5000ms

	# add fifos to the other two bands so we can have some stats
	#/sbin/tc qdisc add dev eth0 parent 1:1 handle 11: pfifo
	#/sbin/tc qdisc add dev eth0 parent 1:2 handle 12: pfifo

	# add a filter so DIP's within the house go to prio band #1 instead of being assigned by TOS
	# thus traffic going to an inhouse location has top priority
	/sbin/tc filter add dev eth0 parent 1:0 prio 1 protocol ip u32 match ip dst 192.168.168.0/24 flowid 1:1

	# multicasts also go into band #1, since they are all inhouse (and we don't want to delay ntp packets and mess up time)
	/sbin/tc filter add dev eth0 parent 1:0 prio 1 protocol ip u32 match ip dst 224.0.0.0/4 flowid 1:1

	# interactive session (not scp) ssh packets go to band #2.
	# (scp sets the IP TOS/diffserv flags to indicate bulk traffic, which allow us to tell it apart from ssh)
        /sbin/tc filter add dev eth0 parent 1:0 prio 2 protocol ip u32 match ip protocol 6 0xff \
                                                                       match ip sport 22 0xffff \
                                                                       match ip tos 0x10 0xff \
                                                                       flowid 1:2
        /sbin/tc filter add dev eth0 parent 1:0 prio 2 protocol ip u32 match ip protocol 6 0xff \
                                                                       match ip dport 22 0xffff \
                                                                       match ip tos 0x10 0xff \
                                                                       flowid 1:2


	# small IP packets go to band #2
	# by small I mean <128 bytes in the IP datagram, or in other words, the upper 9 bits of the iph.tot_len are 0
	# note: this completely fails to do the right thing with fragmented packets. However
	# we happen to not have many (any? icmp maybe, but tcp?) fragmented packets going out the DSL line
	/sbin/tc filter add dev eth0 parent 1:0 prio 2 protocol ip u32 match u16 0x0000 0xff80 at 2 flowid 1:2

	# a final catch-all filter that redirects all remaining ip packets to band #3
	# presumably all that is left are large packets headed out the DSL line, which are
	# precisly those we wish to rate limit in order to keep them from filling the
	# DSL modem's uplink egress queue and keeping the shorter 'interactive' packets from
	# getting through
	# the dummy match is required to make the command parse
	/sbin/tc filter add dev eth0 parent 1:0 prio 3 protocol ip u32 match u8 0 0 at 0 flowid 1:3

	# have the rest of the house think we are the gateway
	# the reason I use arpspoofing is that I want automatic failover to the real gateway
	# should this machine go offline, and since the real gateway does not do vrrp, I hack
	# the network and steal its arp address instead
	# It takes 5-10 seconds for the failback to happen, but it works :-)
	/usr/sbin/arpspoof -i eth0 192.168.168.1 >/dev/null 2>&1 &
	echo $! >/var/run/shapedsl.arpspoof.pid
	;;
    stop)
	/sbin/tc qdisc del dev eth0 root 2>/dev/null
        if [ -r /var/run/shapedsl.arpspoof.pid ]; then
	  kill `cat /var/run/shapedsl.arpspoof.pid`
	  rm /var/run/shapedsl.arpspoof.pid
	fi
	;;
    restart)
	$0 stop
	$0 start
	;;
    *)
    	echo "Usage: $0 [start|stop|restart]"
	exit 1
esac

exit 0  

```


Let me add that while I am NOT a guru of any kind, I have no fear of using a script like this, or of editing startup files.  I just don't know where to start, and I'm afraid of really screwing up the system by blind dabbling!  If someone can tune this script up for today's Ubuntu, it would be a great thing to leave here for EVERYONE to use!  Lord knows, there are plenty of posts on this forum, asking for advice and help with traffic shaping!

---

