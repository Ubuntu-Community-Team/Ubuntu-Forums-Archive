---
title: "so close... yet so far : ipv6 woes"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by jswan on 2006-04-12
I've been having some problems with my wired ethernet connection on my desktop.  I had similar problems on my laptop but it all worked itself out when I renamed the ipv6.ko driver.  

So far I have been following the sticky at the top of the forum to try and fix my problem

After messing around with this and trying the ipv6.ko renaming I had no success.  So instead (I named ipv6.ko back to original) I added to my aliases

alias net-pf-10 off
instead of
#alias net-pf-10 ipv6

The problem continued.
Next I went into firefox and went to the about:config and manually disabled the ipv6 for firefox

FINALLY FIREFOX WORKED but nothing else.  (except I can ping from terminal anything)

So basically this is where I am.  My next goal is pretty much to just be able to apt-get update  so I can get start installing some packages.

Any help would be VERY appreciated! :mrgreen: 


```
$ sudo mii-tool eth1
SIOCGMIIPHY on 'eth1' failed: Operation not supported

```

```
$ lspci | grep Eth
0000:01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)

```

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp


iface eth0 inet dhcp


auto eth1

```

```
$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:01:29:D3:07:A6

```

---

### Post by souki on 2006-04-12
did you try a static configuration of your interface ?

I have ipv6 enabled in /etc/modprobe.d/
ipv6 disabled in firefox

---

### Post by jswan on 2006-04-13
Okay, I tried setting up a static IP and that didn't help at all.  This is what is really killing me

```
$ sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

```

Why is that 1.0.0.0 there!!  I gotta assume that the name translation is getting messed up

```
$ ping www.archive.ubuntu.com
PING www.archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from www.archive.ubuntu.com (82.211.81.182): icmp_seq=1 ttl=51 time=123 ms
64 bytes from www.archive.ubuntu.com (82.211.81.182): icmp_seq=2 ttl=51 time=121 ms
64 bytes from www.archive.ubuntu.com (82.211.81.182): icmp_seq=3 ttl=51 time=122 ms

--- www.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 121.885/122.633/123.302/0.647 ms

```

I have my reposities set exactly how its recommended on the sticky under the repository forums.

any ideas?

---

### Post by souki on 2006-04-13
can you post your /etc/resolv.conf ?

it looks like apt cannot do dns queries, maybe to fast, maybe it's your modem or your ISP

if your dns server is on the modem, you can try to change your /etc/resolv.conf and put your IDPS's dns in it
```
nameserver *your.isp.dns.server*
```
if it doesn't work, you can try to put the archive host in /etc/hosts (so you can at least update your system)
```
82.211.81.182 www.archive.ubuntu.com
```

it is pure speculation, for I don't know about you configuration (hardware and /etc/resolv.conf), but these tests could help to understand what's going wrong

~cheers

---

### Post by jswan on 2006-04-14
How do I find my isp dns servers address?  Its BellSouth by the way

Also, adding in the ip for archive.ubuntu.com did work, thanks for that bit

---

### Post by jswan on 2006-04-14
nevermind I found it in my routers status

EDIT:  Thanks Souki, it worked like a charm!  Stupid modem...

---

### Post by souki on 2006-04-14
great!
you should check for a firmware update or hardware support with your provider or modem manufactor

---

