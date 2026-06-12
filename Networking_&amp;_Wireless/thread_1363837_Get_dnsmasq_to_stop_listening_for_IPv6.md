---
title: "Get dnsmasq to stop listening for IPv6?"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by memilanuk on 2009-12-25
Hello,

I have dnsmasq installed on Ubuntu 9.10 server, and while working through an iptables howto I ran one of the commands therein (lsof) and here is what I found:
```

monte@rahvin:~$ sudo lsof -i -n -P
[sudo] password for monte: 
COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient3 3985    root    5u  IPv4   7234      0t0  UDP *:68 
sshd      4076    root    3u  IPv4   7435      0t0  TCP 10.0.0.1:22 (LISTEN)
dnsmasq   4109 dnsmasq    5u  IPv4   7518      0t0  UDP *:67 
dnsmasq   4109 dnsmasq    6u  IPv4   7525      0t0  UDP *:53 
dnsmasq   4109 dnsmasq    7u  IPv4   7526      0t0  TCP *:53 (LISTEN)
[COLOR="Red"]dnsmasq   4109 dnsmasq    8u  IPv6   7527      0t0  UDP *:53 
dnsmasq   4109 dnsmasq    9u  IPv6   7528      0t0  TCP *:53 (LISTEN)[/COLOR]
sshd      4114    root    3r  IPv4   7581      0t0  TCP 10.0.0.1:22->10.0.0.2:56682 (ESTABLISHED)
sshd      4170   monte    3u  IPv4   7581      0t0  TCP 10.0.0.1:22->10.0.0.2:56682 (ESTABLISHED)
monte@rahvin:~$
```

It *looks* like to me that dnsmasq is listening for IPv6 stuff... which since I have nothing that uses ipv6 nor do I plan on, I would just as soon not have it listening for.  Any ideas how to remedy that?  I haven't been able to find anything related in the dnsmasq config file yet, but I did find someplace where someone suggested putting the following in /etc/sysctl.conf:

```

net.ipv6.conf.all.disable_ipv6 = 1

```

I restarted networking services and dnsmasq and it didn't seem to make any difference.

Ideas?

TIA,

Monte

---

### Post by Iowan on 2009-12-25
I found [this]("http://lists.thekelleys.org.uk/pipermail/dnsmasq-discuss/2005q2/000229.html") in [Dnsmasq-discuss]. It appears that IPv6 support is compiled in/out.

---

### Post by memilanuk on 2009-12-25
Hmmm... nuts :(

So unless I want to 'roll my own' and compile my own version of dnsmasq, I'm stuck with ipv6 whether I want it or not?  Not cool.

Monte

---

