---
title: "Ping domain name slow, ping ip fast, nslookup fast, what's the problem"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by yangxiao on 2009-12-17
ping domain name
```
$ time ping www.cc98.org -c 4
PING alpha.cc98.org (10.10.98.98) 56(84) bytes of data.
64 bytes from 10.10.98.98: icmp_seq=1 ttl=123 time=10.7 ms
64 bytes from 10.10.98.98: icmp_seq=2 ttl=123 time=8.20 ms
64 bytes from 10.10.98.98: icmp_seq=3 ttl=123 time=0.826 ms
64 bytes from 10.10.98.98: icmp_seq=4 ttl=123 time=0.548 ms

--- alpha.cc98.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15097ms
rtt min/avg/max/mdev = 0.548/5.082/10.755/4.488 ms

real    0m16.124s
user    0m0.010s
sys    0m0.000s
```

ping domain name without getting symbolic name
```
$ time ping -n www.cc98.org -c 4
PING alpha.cc98.org (10.10.98.98) 56(84) bytes of data.
64 bytes from 10.10.98.98: icmp_seq=1 ttl=123 time=0.888 ms
64 bytes from 10.10.98.98: icmp_seq=2 ttl=123 time=9.42 ms
64 bytes from 10.10.98.98: icmp_seq=3 ttl=123 time=4.59 ms
64 bytes from 10.10.98.98: icmp_seq=4 ttl=123 time=7.48 ms

--- alpha.cc98.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 0.888/5.596/9.422/3.216 ms

real    0m3.020s
user    0m0.000s
sys    0m0.000s
```

ping ip address is fast
```
$ time ping 10.10.10.98 -c 4
PING 10.10.10.98 (10.10.10.98) 56(84) bytes of data.
64 bytes from 10.10.10.98: icmp_seq=1 ttl=123 time=0.759 ms
64 bytes from 10.10.10.98: icmp_seq=2 ttl=123 time=2.27 ms
64 bytes from 10.10.10.98: icmp_seq=3 ttl=123 time=2.01 ms
64 bytes from 10.10.10.98: icmp_seq=4 ttl=123 time=0.620 ms

--- 10.10.10.98 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 0.620/1.417/2.270/0.734 ms

real    0m3.026s
user    0m0.000s
sys    0m0.000s
```


nslookup is fast
```
$ time nslookup www.cc98.org
Server:        10.214.10.139
Address:    10.214.10.139#53

Non-authoritative answer:
www.cc98.org    canonical name = alpha.cc98.org.
Name:    alpha.cc98.org
Address: 10.10.98.98


real    0m0.014s
user    0m0.000s
sys    0m0.010s
```
What's the problem?

---

### Post by thegner on 2010-01-22
Hi yangxiao,

I know it's a little late, but I was researching the same issue and discovered the reason. It is slow because for each packet returned, the ping program is attempting to do a reverse dns lookup on the IP address to display the name in the "response from..." line. Ping's -n option disables the reverse lookup, thereby reducing the amount of time that passes before the next packet is sent.

You can test this theory by running:
```
nslookup 10.10.98.98
```

Chances are you'll not get the remote host's name in a response. If you have access to your dns server, you'll have to create a reverse dns zone, and a PTR record for 98.98.10.10.in-addr.arpa and point it to [www.cc98.org](www.cc98.org).

Hope this helps to explain what is happening!

Travis Hegner

---

### Post by phisher1 on 2010-02-17
> **thegner said:**
> Hi yangxiao,

I know it's a little late, but I was researching the same issue and discovered the reason. It is slow because for each packet returned, the ping program is attempting to do a reverse dns lookup on the IP address to display the name in the "response from..." line. Ping's -n option disables the reverse lookup, thereby reducing the amount of time that passes before the next packet is sent.

You can test this theory by running:
```
nslookup 10.10.98.98
```

Chances are you'll not get the remote host's name in a response. If you have access to your dns server, you'll have to create a reverse dns zone, and a PTR record for 98.98.10.10.in-addr.arpa and point it to [www.cc98.org](www.cc98.org).

Hope this helps to explain what is happening!

Travis Hegner

Excellent! Thank you. This annoyed the hell out of me too.

---

### Post by mendhak on 2010-07-13
> **thegner said:**
> Hi yangxiao,

I know it's a little late, but I was researching the same issue and discovered the reason. It is slow because for each packet returned, the ping program is attempting to do a reverse dns lookup on the IP address to display the name in the "response from..." line. Ping's -n option disables the reverse lookup, thereby reducing the amount of time that passes before the next packet is sent.

You can test this theory by running:
```
nslookup 10.10.98.98
```Chances are you'll not get the remote host's name in a response. If you have access to your dns server, you'll have to create a reverse dns zone, and a PTR record for 98.98.10.10.in-addr.arpa and point it to [www.cc98.org]("http://www.cc98.org").

Hope this helps to explain what is happening!

Travis Hegner

Late, I know, but this post helped me.  Thank you, doing a 

ping -n servername

made a big difference.

---

### Post by choylee on 2010-12-07
Hello,

How can I disable the reverse DNS on client DNS ? 

I just want to do DNS Standard query A 

Thanks

---

### Post by thegner on 2010-12-07
> **choylee said:**
> Hello,

How can I disable the reverse DNS on client DNS ? 

I just want to do DNS Standard query A 

Thanks

Hi choylee, I don't believe it is easily possible (or desirable for that matter) to disable reverse DNS lookups system-wide.

If you want to only disable any reverse DNS lookups for the ping command, I suppose you could create an alias for ping in you .bashrc:

```
alias ping='ping -n'
```

That would default the ping command to never do reverse DNS lookups.

HTH,

Travis

---

### Post by dschuett on 2011-02-01
I know this post is a bit old, but I just set up my first bind9 dns server on ubuntu 10.04 and I'm having this SAME exact problem with ALL of my internal hosts. If I ping any host that I have set up within bind, it returns with REALLY slow pings... Is there any way to fix this so pings return at a normal speed with my hosts?

I have posted my configs below just in case:

scs.local.db:
```

$TTL 3D
@ IN SOA ubuntu-VM.scs.local. admin.scs.local. (
2007031001;
28800;
3600;
604800;
38400
);

scs.local.    IN   NS      ubuntu-VM.scs.local.
ubuntu-VM     IN   A       192.168.0.150
greenmachine  IN   A       192.168.0.201
gateway       IN   A       192.168.0.1
www           IN   CNAME   greenmachine

```

rev.0.168.192.in-addr.arpa:
```

$TTL 3D
@ IN SOA ubuntu-VM.scs.local. admin.scs.local. (
2007031001;
28800;
604800;
604800;
86400
);


                IN    NS    ubuntu-VM.scs.local.
150             IN    PTR   ubuntu-VM.scs.local.
201             IN    PTR   greenmachine.scs.local.
1               IN    PTR   gateway.scs.local.

```


/etc/bind/named.conf.local:
```

#FORWARD LOOKUP ZONE
zone "scs.local"
{
        type master;
        file "/etc/bind/zones/scs.local.db";
};


#REVERSE LOOKUP ZONE
zone "0.168.192.in-addr.arpa"
{
        type master;
        file "rev.0.168.192.in-addr.arpa";
};

```

/etc/bind/named.conf.options:
```

options {
        directory "/var/cache/bind";

        forwarders {
        8.8.8.8;
        8.8.4.4;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

---

### Post by thegner on 2011-02-03
Hi dschuett,

Assuming a command like ```
ping -n greenmachine.scs.local
``` correctly resolves to an IP address, and pings quickly like you'd expect, then there must be a problem with your reverse DNS.

Double check the reverse zone in /etc/bind/named.conf.local.

On first glance, it appears you are referencing a relative filename, while in the forward zone you are specifying an absolute filename. If the "rev.0.168.192.in-addr.arpa" file is in the "zones" directory, like the forward lookup file, then you're problem can be solved by changing the "file" line in the reverse zone to: ```
file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
```

HTH,
Travis

---

### Post by wallyweek on 2011-02-28
> **thegner said:**
> 
It is slow because for each packet returned, the ping program is attempting to do a reverse dns lookup on the IP address to display the name in the "response from..." line. Ping's -n option disables the reverse lookup, thereby reducing the amount of time that passes before the next packet is sent.
Travis Hegner

I know 1 month has passed since this post, but I definitely need to thank you, you saved my life after weeks looking around for an answer!

God bless you!

Cesare.

---

