---
title: "XBMC live - DNS not working"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by blm14 on 2010-03-06
Hey all! I installed XBMC live and stupidly skipped the networking configuration. So I manually added the entries for eth0 in /etc/network/interface, which looks like this now:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.80
netmask 255.255.255.0
gateway 196.168.1.1

```I can SSH to the machine and it can ping IP addresses on my local network. So far so good. It couldn't connect to ANY hosts, so I did this:

```

sudo route add default eth0
```So now it attempts to look up hosts but fails every time:

```

xbox@XBMCLive:~$ sudo apt-get update
0% [Connecting to archive.ubuntu.com] [Connecting to www.lonelycoder.com] [Connecting to ppa.launchpad.net]

```And it just sits there like that until I control-C.

Here is the content of /etc/resolv.conf:

```

xbox@XBMCLive:~$ more /etc/resolv.conf
#domain dummy.net
domain nyc.res.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 24.29.103.15

```My questions are this:

1) How can I make "route" automatically use eth0 so I don't have to specify it each time at boot

2) Why is DNS not working and how do I fix it? Thanks!

---

### Post by blm14 on 2010-03-06
Oh, almost forgot - this might be helpful:

```

xbox@XBMCLive:~$ uname -a
Linux XBMCLive 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

```

---

