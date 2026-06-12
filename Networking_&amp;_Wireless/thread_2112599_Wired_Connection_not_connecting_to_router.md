---
title: "Wired Connection not connecting to router"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by SeanW95 on 2013-02-05
Hello I've recently installed ubuntu on a 20GB partition using the windows based installer. I booted up and It won't connect to my network( Ethernet direct to router/modem AIO unit.)I've been talking in the IRC which had alot of help but no solutions. Any help?

To give a little background I like to think I'm quite proficient in the windows environment and currently on my last year studying a BTEC IT course (Level 3 extended diploma) and this is my first time on linux without suppourt from a tutor. I wanted to get a feel for linux and have very little knowledge of linux.
I'm running Ubuntu 12.10

EDIT: Information such as ifconfig is in the posts below!

---

### Post by SeanW95 on 2013-02-07
Edit : installed without wubi still same error. It says connected but I can't ping my router

---

### Post by Warren Hill on 2013-02-07
There are lots of reasons for possible problems and we need more to go on
open a terminal (CTRL+ALT+T) and enter the following it may give us a clue 

```


lsb_release -a; uname -a; sudo lshw -C network; ifconfig; route -n; cat \etc\network\interfaces


```Post all the results back here and we may be able to advise further

---

### Post by SeanW95 on 2013-02-07
As you requested.
Lsb_Release -a
```
sean@sean-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

```
uname -a
```
sean@sean-ubuntu:~$ uname -a
Linux sean-ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```
ifconfig
```
sean@sean-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:08:03:6c  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe08:36c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7345 (7.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34320 (34.3 KB)  TX bytes:34320 (34.3 KB)

```
route -n
```
sean@sean-ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

---

### Post by Warren Hill on 2013-02-07
Looking good so far.  Try 

```
ping -c5 192.168.0.1; ping -c5 8.8.8.8
```

---

### Post by SeanW95 on 2013-02-07
Does it make any difference that my motherboard is a Nforce 630a chipset? and here are my ping results.
```
sean@sean-ubuntu:~$ ping 0c5 192.168.0.1
ping: unknown host 0c5
sean@sean-ubuntu:~$ ping 192.168.0.1 -c5
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.25 icmp_seq=1 Destination Host Unreachable
From 192.168.0.25 icmp_seq=2 Destination Host Unreachable
From 192.168.0.25 icmp_seq=3 Destination Host Unreachable
From 192.168.0.25 icmp_seq=4 Destination Host Unreachable
From 192.168.0.25 icmp_seq=5 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 3999ms
pipe 3
sean@sean-ubuntu:~$ ping 8.8.8.8 -c5
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.25 icmp_seq=1 Destination Host Unreachable
From 192.168.0.25 icmp_seq=2 Destination Host Unreachable
From 192.168.0.25 icmp_seq=3 Destination Host Unreachable
From 192.168.0.25 icmp_seq=4 Destination Host Unreachable
From 192.168.0.25 icmp_seq=5 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 3999ms
pipe 3

```

---

### Post by PowerBarry43 on 2013-02-07
Hi

this route looks suspicious

```
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```Normally where it says 0.0.0.0 I'd expect to see "default" but I would expect this to work too.

Also because you're getting unreachables from your own ip we know that your machine doesnt know what to do with these pings which indicates a routing/default gateway problem.

We can try remove this suspicious route and adding it back again correctly to rule it out as a cause. Just fire up a terminal and run:

```
route del 0.0.0.0
route add default gw 192.168.0.1
```Hope this helps!

Barry

---

### Post by fj401971 on 2013-02-07
I don't know about that...my routes look similar to the problematic ones and I'm having no problems with my connection.  The only thing different is the metrics and the interface.

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by fj401971 on 2013-02-07
And just to ask the obvious question, your router is setup to respond to pings?

---

### Post by SeanW95 on 2013-02-08
Command didn't work...and yes my router responds to pings
```
sean@sean-ubuntu:~$ route del 0.0.0.0
SIOCDELRT: Operation not permitted
sean@sean-ubuntu:~$ soute add default gw 192.168.0.1
No command 'soute' found, did you mean:
 Command 'route' from package 'net-tools' (main)
soute: command not found
sean@sean-ubuntu:~$ route del 0.0.0.0
SIOCDELRT: Operation not permitted
sean@sean-ubuntu:~$ route add default gw 192.168.0.1
SIOCADDRT: Operation not permitted
sean@sean-ubuntu:~$ sudo route del 0.0.0.0
[sudo] password for sean: 
SIOCDELRT: No such process
sean@sean-ubuntu:~$ sudo route add default gw 192.168.0.1

```

---

### Post by fdrake on 2013-02-08
change the gateway to 192.168.1.1 and the destination to default.
```
route add default gw 192.168.1.1
ping 192.168.1.1

```


btw : what router(model) are you using?

---

### Post by SeanW95 on 2013-02-08
My gateway is 192.160.0.1 not x.x.1.1 ? And skys sagemcom router. Can't give exact model I'm on mobile.

---

### Post by Warren Hill on 2013-02-08
How are you connected to the internet?

Are you using the same computer and router as the one you are having problems with?  If yes is this in Ubuntu or are you booting into another OS?

It appears that your router is not responding.

Most likely causes for this are

1.  Faulty router - unlikely if you are using this router to connect from the same or another computer

2. Faulty connection - unlikely if you are using the same computer, even if you have to boot into another OS

3.  Misconfiguration - If you can connect from another computer or OS it may be worth checking its settings

4. Firewall getting in the way for example

Tell us more about your setup and we may be able to advise more

---

### Post by SeanW95 on 2013-02-08
*How are you connected to the internet?*
_- ethernet from desktop onboard NIC to modem/router._
*Are you using the same computer and router as the one you are having problems with? If yes is this in Ubuntu or are you booting into another OS?*
 _Yes I am. I have a dualboot with windwows 7 and ubuntu. I'm Booting into ubuntu on my desktop_

[I]It appears that your router is not responding.

Most likely causes for this are[/I]

*1. Faulty router - unlikely if you are using this router to connect from the same or another computer*
_- works fine in windows 7 and with xbox360 & windows 8 laptop._

*2. Faulty connection - unlikely if you are using the same computer, even if you have to boot into another OS*
_- Plugged in a new ethernet cable and interface on the router/modem._

*3. Misconfiguration - If you can connect from another computer or OS it may be worth checking its settings*
_- I could post my router settings etc?_


*4. Firewall getting in the way for example*
_- Firewall disabled._

---

### Post by Warren Hill on 2013-02-08
Most likely problem is configuration so to find out what your working windows 7 is set to 

click the start button  and type cmd in the search box 

In the window that opens type 

```
ipconfig /all
```

Post all the results back here

Now with your Ubuntu boot open a terminal and give us the output of

```
cat /etc/network/interfaces
```

This probably needs to be edited and hopefully we will be able to tell you what it should contain.

---

### Post by SeanW95 on 2013-02-08
**ipconfig **
```
http://pastebin.ca/2311836
```

**interfaces**
```
sean@sean-ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by Warren Hill on 2013-02-08
I can't see why this isn't working 

Your windows machine is set to get its network settings automatically by DHCP and its getting the following settings

```
 
Physical Address. . . . . . . . . : BC-5F-F4-08-03-6C
DHCP Enabled. . . . . . . . . . . : Yes
IPv4 Address. . . . . . . . . . . : 192.168.0.25(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.0.1

```Your Ubuntu machine is set to get its network settings automatically by DHCP and its getting the following settings

```
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:08:03:6c             
          inet addr:192.168.0.25  
          Bcast:192.168.0.255  
          Mask:255.255.255.0
```And the default gateway is 

```
sean@sean-ubuntu:~$ route -n Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0 

```These are the same so it looks like configuration is working properly.
so you should be able to ping not only the router but anywhere on the network or internet.

Is the ubuntu firewall enabled? to check what's the output of 

```
sudo ufw status; nm-tool
```

---

### Post by SeanW95 on 2013-02-08
**UFW status**
```
sean@sean-ubuntu:~$ sudo ufw status
Status: inactive
```

**NM -TOOL**
```
sean@sean-ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        BC:5F:F4:08:03:6C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

```

---

### Post by PowerBarry43 on 2013-02-08
Hi

I notice in your earllier post you show the output of route add and del commands but you get an error messeage "SIOCDELRT: No such process"

An identical error appears in this thread:

[http://ubuntuforums.org/showthread.php?t=1318743](http://ubuntuforums.org/showthread.php?t=1318743)

which is solved by running


```
sudo [text editor of choice] /etc/hosts
```then adding a line saying

```
192.168.0.25    sean-ubuntu
```on line three at the end of the ipv4 block.

and restarting the networking service with


```
sudo service networking restart
```
 Seems to have worked there so maybe give that a shot. :wink:
Hope this helps!

Barry

---

