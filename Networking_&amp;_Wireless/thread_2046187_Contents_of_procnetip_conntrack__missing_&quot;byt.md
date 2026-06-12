---
title: "Contents of /proc/net/ip_conntrack  missing &quot;bytes=&quot; and &quot;packets=&quot;?"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by funcrusher on 2012-08-22
Hi all,

I'm trying to set up a script that will monitor the bandwidth being used by a given process and kill it if it exceeds a threshold. I was planning on using bwmon ([http://thp.io/2010/bwmon/](http://thp.io/2010/bwmon/)), which reads /proc/net/ip_conntrack to get the number of bytes in each packet and the packet count.

The first thing I noticed was that /proc/net didn't contain ip_conntrack, so then I tried:

```
~$ sudo modprobe ip_conntrack
```This at least gives me an ip_conntrack, but it's missing the "bytes=" and "packets=" fields. From googling I expect each entry to look something like this:

```
~$ sudo tail -n 1 /proc/net/ip_conntrack
tcp      6 431557 ESTABLISHED src=X.X.X.X dst=X.X.X.X sport=44242  dport=993 packets=128 bytes=9267 src=X.X.X.X dst=X.X.X.X sport=993  dport=44242 packets=85 bytes=53950 [ASSURED] mark=0 use=2
```but what I actually get looks like this:

```
~$ sudo tail -n 1 /proc/net/ip_conntrack
tcp      6 431665 ESTABLISHED src=X.X.X.X dst=X.X.X.X sport=4640  dport=8082 src=X.X.X.X dst=X.X.X.X sport=8082 dport=4640 [ASSURED]  mark=0 use=2
```I'm running 12.04 and kernel v3.2.0-29, but I also find that the entries look the same (i.e. missing "bytes=" and "packets=") on another machine running 11.04 and kernel v3.0.0-23.

So what gives? Is there some way I can turn on logging of packet size/count, or is this information now being logged somewhere else?

---

### Post by waltermundt on 2012-08-24
It's been awhile, but I ran into this post based on a Google search, along with another [over in Gentoo-land]("http://forums.gentoo.org/viewtopic-p-6677939.html") that suggests the following:

```
sysctl -w net.netfilter.nf_conntrack_acct=1
```

No time to test it right now, but I thought I'd drop it here in case anyone else follows the same path I did with this question, or the original poster still cares.

---

### Post by funcrusher on 2012-08-24
Nice, that seemed to do the trick:  bytes= and packets= are now reported in /proc/net/ip_conntrack.

For anyone else who might be interested, I added ip_conntrack to /etc/modules so that it loads at boot time, and I added net.netfilter.nf_conntrack_acct=1 to /etc/sysctl.conf to make logging of packet size and count persistent.

---

### Post by Doug S on 2012-08-24
Interesting thread. My main server is still at ubuntu server version 10.10, and that version defaults to include byte and packet count in the conntrack table listings. As this thread says, my two test 12.04 servers default to not include the counts. So it appears it was a change between 10.10 and 11.04. I always want the counts, so I will do as funcrusher did. However, in my case, I don't think the change to /etc/modules is needed.

---

