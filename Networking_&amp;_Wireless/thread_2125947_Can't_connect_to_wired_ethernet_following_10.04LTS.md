---
title: "Can't connect to wired ethernet following 10.04LTS to 12.04LTS upgrade"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by Spacecoaster on 2013-03-15
Hi all,

I've upgraded from 10.04LTS to 12.04LTS on my desktop and now my ethernet connection doesn't work.  The connection still works fine if I boot from the 10.04 CD but won't connect from the desktop version of 12.04.  I've attached ifconfig output from both.

I can successfully ping the router and the response time is pretty much the same from the 10.04 CD boot as from the 12.04 desktop.  There is no packet loss in 12.04.  However, I can't view the router's set up menu or anything beyond it in Firefox.  

I don't have wireless on the desktop so I can't check for software updates from that computer (I'm posting from my work laptop).

Assistance would be most welcome.

Cheers

---

### Post by Bashing-om on 2013-03-15
Spacecoaster; Hi ! Welcome to the forum.

You have the same IP address on both boxes - no can do, confuses the router muchly.[both connected to router ???]
Try this:
12.04 : right click on the connections icon in the task bar ->choose edit connections;
click on your wired connection ->edit;
wired: MTU = Automatic
ipv4 settings: -> set in methods box : Automatic (DHCP) and "available to all users" check box (lower left corner) checked.
ipv6 settings: -> Automatic and ditto on available to all users.
Reboot for the changes to take effect.
------------
I expect then that the 12.04 box will receive a new address from the router.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Spacecoaster on 2013-03-15
Thanks for the welcome, Bashing-om!  

Unfortunately, I've just tried your suggestion and sadly no improvement.

I'm not sure what you mean by both boxes?  There is only one box: it has 12.04 installed.  However  I was able to confirm that the physical ethernet connection is OK by running 10.04 on this machine directly from the old 10.04 installation disc.  I guess this explains the IP addresses being the same or could this still be part of the problem?

---

### Post by Bashing-om on 2013-03-15
Spacecoaster;
Connecting through a router ?
Yes -> suggestion: access the router through the browser and maybe there is an option to "clone" the IP address of the computer.(that is what I had to do to get my box up on the net)
[INDENT=2]
try'n to help

[/INDENT]

---

### Post by Spacecoaster on 2013-03-15
Yes, I'm connecting through a router.  Alas, I don't have control over it.  It's operated by the landlord of the apartment compound I live in.  I'm not making things easy, am I?!

---

### Post by Bashing-om on 2013-03-15
Spacecoaster; If everything were "easy" we would all be babbling away in a far corner.

OK, one step at a time, lets see if your computer can talk to the router. 
terminal code:
```
route
``` returns  an address(amongst other info) at the intersection of default and gateway (like 192.168.0.1)
then from terminal talk to that router: Substitute your own gateway address in code below.
```
 ping -c 3 192.168.0.1
``` final result we want is: "3 packets transmitted, 3 received, 0% packet loss, time 2001ms"[INDENT=2]not there yet

     
[/INDENT]

---

### Post by Spacecoaster on 2013-03-16
Results from route
[INDENT]Kernel IP routing table[/INDENT]
[INDENT]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/INDENT]
[INDENT]default         192.168.100.1   0.0.0.0         UG    0      0        0 eth0[/INDENT]
[INDENT]link-local      *               255.255.0.0     U     1000   0        0 eth0[/INDENT]
[INDENT]192.168.100.0   *               255.255.255.0   U     1      0        0 eth0[/INDENT]

and ping
[INDENT]PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.[/INDENT]
[INDENT]64 bytes from 192.168.100.1: icmp_req=1 ttl=64 time=3.39 ms[/INDENT]
[INDENT]64 bytes from 192.168.100.1: icmp_req=2 ttl=64 time=1.01 ms[/INDENT]
[INDENT]64 bytes from 192.168.100.1: icmp_req=3 ttl=64 time=1.41 ms[/INDENT]
[INDENT]
[/INDENT]
[INDENT]--- 192.168.100.1 ping statistics ---[/INDENT]
[INDENT]3 packets transmitted, 3 received, 0% packet loss, time 2002ms[/INDENT]
[INDENT]rtt min/avg/max/mdev = 1.010/1.938/3.394/1.042 ms[/INDENT]

Ping result seems to be pretty close to what you were expecting, Bashing-om.  I hope this is a good sign!

---

### Post by Bashing-om on 2013-03-16
Spacecoaster;
 That looks promising with confirmation you are getting out of your computer and talking to the router. Most likely now just a matter of configurations. Let's see that DNS (domain name service) lookup is functioning:

```
 ping -c 3 74.125.225.232
ping -c 3 google.com
```

If the IP returns and the name does not, then we need to give the network manager a domain name.[INDENT=2]
we stepp'n

[/INDENT]

---

### Post by Spacecoaster on 2013-03-16
Yes, the IP returns but the name does not (it returns unknown host google.com).  How do we give network manager a domain name?

---

### Post by papibe on 2013-03-16
Hi Spacecoaster.

It's looking like a DNS problem.

Could you post the result of these commands?
```
cat /etc/resolv.conf

grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```
Regards.

---

### Post by Spacecoaster on 2013-03-16
Hi pabibe

Results as follows:

cat /etc/resolv.conf

[INDENT]# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)[/INDENT]
[INDENT]#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN[/INDENT]
[INDENT]nameserver 127.0.0.1
[/INDENT]

grep dnsmasq /etc/NetworkManager/NetworkManager.conf

[INDENT]
dns=dnsmasq
[/INDENT]

cat /var/run/nm-dns-dnsmasq.conf

[INDENT]server=192.168.100.1[/INDENT]
[INDENT]server=198.41.0.4
[/INDENT]

I hope this lot makes sense to you?  Thanks!

---

### Post by papibe on 2013-03-16
Thanks.

Try this:
```
sudo service network-manager stop

sudo dpkg-reconfigure resolvconf

sudo service network-manager start
```
Let us know how it goes.
Regards.

---

### Post by Spacecoaster on 2013-03-17
papibe:

I've just tried your suggestion.  Unfortunately, no change in the network connection, even following reboot.    I said 'yes' to enabling  dynamic linking on resolvconf during the reconfigure - I hope this was the correct thing to do?

---

### Post by papibe on 2013-03-17
That's not good.

Try disabling the dnsmasq plugin on Network Manager. Read [here]("http://ubuntuforums.org/showpost.php?p=11923702&postcount=40").

Let us know how it goes.
Regards.

---

### Post by Spacecoaster on 2013-03-17
papibe: good news, disabling dnsmasq seems to have worked!  Thanks so much to you and Bashing-om for your assistance!

As an aside, I didn't think it had been successful at first because firefox still wouldn't connect to the web. To double check I tried:

```

ping google.com

```

from the terminal and, to my surprise, that was successful.

Turns out that the firewall (Firestarter) was set to a restrictive outbound policy and my router wasn't listed.  Having changed the outbound policy to permissive, I am now typing this from firefox on my ubuntu machine.  Joy!

Cheers!

---

### Post by Bashing-om on 2013-03-17
Spacecoaster; Outstanding !

Glad you are up on the 'net// Just for info I had 3 "possible" solutions - none of which I liked - as I could not replicate the files on my 12.04 system . Given your solution they would have been ineffective !
[HTML]
cat /var/run/nm-dns-dnsmasq.conf

server=192.168.100.1[/HTML] Could not understand how the router got named as a dns server. Got some more homework to do to understand dnsmasq and the way DNS setup is now handled as the file /etc/resolve.conf is no longer implicitly used for this function.[INDENT=2]
ubuntu, an ever evolving process

[/INDENT]

---

### Post by jdthood on 2013-03-20
Mark this as "SOLVED", then?

---

### Post by Spacecoaster on 2013-03-20
> **jdthood said:**
> Mark this as "SOLVED", then?

Sounds like a good idea.  How do I do that?

---

### Post by mörgæs on 2013-03-20
The function is broken for the time being. I have done it manually.

---

