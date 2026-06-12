---
title: "Server problems after a new router"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by Badbunny on 2011-03-02
I recently replaced my ancient adsl router with a Buffalo WBMR-HP-GN. After changing the router, I am unable to reach any server on my computer, for example minecraft and ssh.

I used this guide:
[http://portforward.com/english/routers/port_forwarding/Buffalo/WBMR-HP-GN/SSH.htm](http://portforward.com/english/routers/port_forwarding/Buffalo/WBMR-HP-GN/SSH.htm)

I have forwarded the ports:
[[IMG]http://img27.imageshack.us/img27/72/portforwards.jpg[/IMG]](http://img27.imageshack.us/i/portforwards.jpg/)

I have also set a static ip:
[[IMG]http://img97.imageshack.us/img97/696/screenshoteditingautoet.png[/IMG]](http://img97.imageshack.us/i/screenshoteditingautoet.png/)

Route gives me this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.11.1    0.0.0.0         UG    0      0        0 eth0

```

Ifconfig gives me this:
```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:ae:5f:4c  
          inet addr:192.168.11.64  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feae:5f4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14169167 (14.1 MB)  TX bytes:3244395 (3.2 MB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5153 (5.1 KB)  TX bytes:5153 (5.1 KB)

```

/etc/network/interfaces reads like so:
```
auto lo
iface lo inet loopback
```
, which looks vaguely weird, but I have no idea why.

Any ideas on what am I doing wrong?

EDIT:
Forgot to mention that ssh connection gives a "connection timed out". And I have tried the Buffalo's DMZ mode, but in vain.

---

### Post by geoffmcc on 2011-03-02
the first thing that jumps out at me is in router you forwarded 22 to 192.168.11.65 but then then your screenshot of network config shows ip address as being 192.168.11.64

but maybe your trying to ssh to a different box?

---

### Post by Badbunny on 2011-03-02
Ah, no, that was a mistake :) Thanks.

Nevertheless, even after I fixed that, the connection keeps timing out.

Looks like this now:
[[IMG]http://img189.imageshack.us/img189/7504/sshfixed.png[/IMG]](http://img189.imageshack.us/i/sshfixed.png/)

And the DMZ window on the router's control panel looks like this:
[[IMG]http://img138.imageshack.us/img138/5060/dmzo.png[/IMG]](http://img138.imageshack.us/i/dmzo.png/)

---

### Post by geoffmcc on 2011-03-02
Yea after i said that i realized something and was working on an edit but it took me so long i figured you would have replied already. 


as long as all computers are pluged into the same router and you are accessing using local address you do not need forwarding
so i guess maybe that is not the issue. Would only need portforwading if you were elsewhere trying to ssh in or if you were using a domain name instead of local address.

---

### Post by Badbunny on 2011-03-02
Ah, sorry for not being clear on that. I am trying to run a server on my computer that is remotely accessible. I get the connection timeout when I try to access the computer from outside. And I'm using a domain name from dyndns, that seems to update just fine.

---

### Post by geoffmcc on 2011-03-02
I assume the firewall is opened on box as all you have done is change the router.

So what about a firewall on the router. I run dd-wrt and it does have a SPI Firewall enabled (although it does not interfere with my ssh connectivity) but maybe worth disabling if there is one and check it out.

P.S- I need to read more carfully i guess as i now notice your original post shows that you even put this computer on the DMZ. That would def eliminate port forwarding issues. I think the answer lies in that security tab, if was working before you put this router on.

---

### Post by Badbunny on 2011-03-02
Yes, the ports are opened on the software firewall.

The router's firewall tab seems a bit limited, I have unchecked all the boxes.
[[IMG]http://img854.imageshack.us/img854/9541/firewall.png[/IMG]](http://img854.imageshack.us/i/firewall.png/)

---

### Post by geoffmcc on 2011-03-02
Yea by the picture everything is 0 packets so router firewall wasn't stooping you, so prob OK to turn back on.

hmm. i would say try turning off firewall completely on the box and give a test but if was firewall blocking it probably wouldn't time out- would say connection refused.

Sorry- you got me stumped (doesn't take much)

---

