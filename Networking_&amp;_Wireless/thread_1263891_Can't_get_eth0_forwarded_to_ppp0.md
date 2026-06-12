---
title: "Can't get eth0 forwarded to ppp0"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by mpetty423 on 2009-09-11
Ok, so here's my dilemma.   I have some machiens set up like this:


[windows box 1](192.168.0.60)<----switched ethernet---->[ubuntu box 1](192.168.0.55) <---ppp link ----> (192.168.0.255) [ubuntu box 2]<-----switched ethernet ---->(192.168.0.33) [network device]

I currently have nearly everything set up.  I can auto-dial the ppp connection, it will connect and work.  I can ping across it, and so on and so forth.

On ubuntu box 2, I have some iptables policies that forward ppp0 to eth0, and it seems to work.  Using tcpdump, I can watch the packet come in on pp0 and go out on eth0.

Now, I was thinking that I needed to do something similar with ubuntu box 1.  I need the packets coming in on eth1 from the windows box to be forwarded to ppp0 to make their way across link to the network device.  The windows box produces packets that the network device eats, essentially.

But I can't seem, no matter what iptables rules I apply to get eth1 packets to appear on ppp0.  I have tcpdump running on both of them, and I either just see the ping request come in on eth1, but never get to ppp0, or I get the message on eth1 
```
arp who-has 192.168.0.33 tell 192.168.0.60
```but never see that message on ppp0.  I know that ppp0 can see 192.168.0.33, because when I don't have the ip tables rules applied, it pings it just fine.

My rules are:

```

iptables -t nat -A POSTROUTING eth1 -j MASQUERADE
iptables -A FORWARD -s 192.168.0.60 -d 0.0.0.0/0 -j ACCEPT
iptables -A FORWARD -i eth1 -o ppp0 -m state --state ESTABLISHED<RELAED -j ACCEPT
iptables -A FORWARD -i ppp0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
```I do have ip_forward set to 1, and Ihave tried proxy_arp set to 1.  I've tried a number of other rules, but just cannot for the life of me get packets coming in on eth1 to go to ppp0!

---

### Post by fwre01 on 2009-09-15
There are lots of things wrong here, I can take a look at it, but I wont write it all out unless you are still having problems? Let me know and ill take a look :-)

Whats the physical medium of the ppp0 interface out of interest?

---

