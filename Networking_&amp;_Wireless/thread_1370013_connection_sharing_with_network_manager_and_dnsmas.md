---
title: "connection sharing with network manager and dnsmasq"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by donwinchell on 2010-01-01
First I will briefly say I am posting here as much to learn how to use the forum as for the technical solution.

the question is; how to change the IP range provided by default by Network Manager / dnsmasq  from 10.42.43.-- to something else?

I have setup a working network using a Bell wireless modem (Canada) and Network Manager in 8.10, 9.04, and 9.10.to do Internet connection sharing.
In 8.10 the only way I could get it to work was with WICD and KPPP, many hours spent on this one.
I got it to work in 9.04 and 9.10 using network manager, but certainly not out-of-the-box. If someone would like some tips on how I did it, in each case, let me know.

My current challenge is trying to set the dhcp range of dnsmasq (which I am 99% sure is what is handing out addresses) from th 10.42.43.-- address range to a 192.168.0.-- range.

I HAVE edited /etc/dnsmasq.conf and can get the edits to this file to break the setup (dnsmasq will not start) but have not been able to get it to change the IP address range.

It seems that either this file is ignored, or overridden by some other process. I have looked at the very good post at help.ubuntu.com about dnsmasq but this does not do the trick.

By the way, the way I can get this to work is to start NM, establish my cellular internet connection, then kill dnsmasq then establish my ICS network (on eth0).  If I don't kill dnsmasq, then it does bring up the connection, but it then shuts down in a matter of seconds.  It is all very manageable using a launcher (kdesudo pkill dnsmasq) on the task bar, but not all that elegant. 

the IP range and where this is provided to Network Manager or the network itself is my real question now.  any help is certainly appreciated.
thanks.

---

### Post by Otto Nascarella on 2010-01-22
Finally someone who's getting the same problem that I am!

Look...it's really weird. I could not find anywhere in the dnsmasq man pages about it.

I've been sharing internet connection between 2 laptops using dnsmasq/network-manager to create the ad-hoc, but could not find out how to use it as a DHCP server despite having configured dnsmasq.conf to do so.

My "work around solution" was to install dhcp3-server, and edit dhcpd.conf to work on the mysterious range 10.42.43.X that's given by dnsmasq/network-manager. so far, it's been working.

But the questions which lingers on are: 

1. where do we change the ip dnsmasq/network-manager is giving to the ad-hoc device??

2. how do we configure dnsmasq so we don't need dhcp3-server!??!


UBUNTU COMMUNITY MASTERS, anyone!? :confused:

---

### Post by »John« on 2010-02-08
> **donwinchell said:**
> 
It seems that either this file is ignored, or overridden by some other process.


For a while I was trying to do the same thing, that's how I got here.

Right now the DHCP range (among other things) seems to be hardcoded in NetworkManager because if you take a look at syslog, you'll see it's actually running iptables several times to set up routing between network interfaces and then launching dnsmasq with custom setup defined by command line arguments, which means whatever tweaks you made to the configuration file get overridden by these.

There may be a way to change this using either global NetworkManager config or applying personal setting using GConf/KConfig, but I haven't Googled anything so far and considering NetworkManager philosophy (everything should "Just Work" as automatically as possible and intrude as little as possible into your workflow), it seems quite unlikely that it already contains required infrastructure. Try asking one of the devs if you absolutely need to know and perhaps suggest this as a potentially useful new feature.

OK, it's really [hardcoded for now]("http://www.mail-archive.com/networkmanager-list@gnome.org/msg13790.html").

---

### Post by Iowan on 2010-02-08
I have **dnsmasq** running on my server (which means no Network Manager). Please post your */etc/dnsmasq.conf*. Which edits broke it?

---

### Post by donwinchell on 2010-02-13
Iowan,
thanks for the reply.  I left this about a month ago as I just changed all ips in my local net to the 10.42.43.0 net.
came back to it recently and found my own post with replies (I guess I had mail notification turned off as I thought this was dead).

In any case I just put in bad values on some of the config lines, none in particular to see if dnsmasq was even reading this file. it was and would cause it not to start.  the "bad lines" were just for testing.

but thanks for your reply.  it looks like, from an earlier post, that network manager IS overriding any IP changes from dnsmasq. so I will just let it go until something changes on that end.

thanks again

---

### Post by Otto Nascarella on 2010-03-03
Ok y'all

I ran many tests in my house and read a couple of posts in different places and what I've learnt is that when you create a ad-hoc connection, network-manager runs dnsmasq with range 10.42.43.X (hard-cored; that's the reason you do not need dnsmasq.conf), then runs iptables in order to forward ports so connection is actually shared (NAT).

The bug:

What was going on wrongly was, that when you bounce your system, if ad-hoc connection is in AUTO mode, network-manager runs dnsmasq before resolv.conf has any DNS information inside it, whereby not "dnsmasquing" at all.

Workaround: 

Before you create a ad-hoc connection in order to share internet, make sure that /etc/resolv.conf has the DNS configuration.
 

I believe the resolv.conf bug will be fixed soon but we still need to suggest implementation so we can choose a WLAN range if we need to.



ciao for now.

---

### Post by Jonathan Provost on 2011-06-13
As a workaround, I have this setup.  It allows me to use something else than 10.42.43.x.  I had to override /usr/sbin/dnsmasq and /sbin/iptables

```

jprovost@localhost:~$ ls /usr/sbin/dnsmasq.bin 
/usr/sbin/dnsmasq.bin
jprovost@localhost:~$ cat /usr/sbin/dnsmasq
#!/bin/bash
SUBNET=192.168.50
INTERFACE=$(ifconfig | grep 10.42.43 -B1 | cut -c1-10)
[ "$INTERFACE" ] && ifconfig $INTERFACE $SUBNET.1
/usr/sbin/dnsmasq.bin $( echo $* | sed 's/10.42.43/'$SUBNET'/g' )
jprovost@localhost:~$ cat /sbin/iptables
#!/bin/bash
SUBNET=192.168.50
INTERFACE=$(ifconfig | grep 10.42.43 -B1 | cut -c1-10)
[ "$INTERFACE" ] && ifconfig $INTERFACE $SUBNET.1
ln -sf /sbin/iptables-multi /tmp/iptables
/tmp/iptables $( echo $* | sed 's/10.42.43/'$SUBNET'/g' )
jprovost@localhost:~$
```

---

### Post by Jonathan Provost on 2011-06-13
As a workaround, I have this setup.  It allows me to use something else than 10.42.43.x.  I had to override /usr/sbin/dnsmasq and /sbin/iptables

```

jprovost@localhost:~$ ls /usr/sbin/dnsmasq.bin 
/usr/sbin/dnsmasq.bin
jprovost@localhost:~$ cat /usr/sbin/dnsmasq
#!/bin/bash
SUBNET=192.168.50
INTERFACE=$(ifconfig | grep 10.42.43 -B1 | cut -c1-10)
[ "$INTERFACE" ] && ifconfig $INTERFACE $SUBNET.1
/usr/sbin/dnsmasq.bin $( echo $* | sed 's/10.42.43/'$SUBNET'/g' )
jprovost@localhost:~$ cat /sbin/iptables
#!/bin/bash
SUBNET=192.168.50
INTERFACE=$(ifconfig | grep 10.42.43 -B1 | cut -c1-10)
[ "$INTERFACE" ] && ifconfig $INTERFACE $SUBNET.1
ln -sf /sbin/iptables-multi /tmp/iptables
/tmp/iptables $( echo $* | sed 's/10.42.43/'$SUBNET'/g' )
jprovost@localhost:~$
```

---

