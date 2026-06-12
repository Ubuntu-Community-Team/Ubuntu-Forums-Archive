---
title: "wired internet/ifconfig problems"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by drfoight on 2009-07-26
Hi all,
   I am having a problem very similar to Newfoundlander ([http://ubuntuforums.org/showthread.php?t=1222245]("http://ubuntuforums.org/showthread.php?t=1222245")), however, while following along with the help offered to him, I found some things that I hope warrant a new thread. So, to sum up, I recently upgraded to 9.04, and the wired internet connection on my desktop computer stopped working. On my desktop, I have the ethernet port from the MB, and a network card that I was using instead of that port for my wired internet connection (formally known as eth0 and 'Wired Connection 1', respectively). The computer has been sitting (in use) without a connection to the internet from either port for ~1 month. 

So, I hook the computer back up to the internet (using 'Wired Connection 1', the network card), and it says that I am connected, but firefox gives errors of the sort "Firefox cannot find the server at ...", and a "ping www.google.com" gives 'ping: unknown host [www.google.com](www.google.com)'. So, going through the song and dance of trying to figure out what is going on, I did the usual 'ifconfig', when I noticed the output is extremely odd, and much different than what I have ever seen before. It is below:

```
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:90:ff:44  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe90:ff44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:584532 (584.5 KB)  TX bytes:308110 (308.1 KB)
          Memory:fdfc0000-fdfe0000 

eth1      Link encap:Ethernet  HWaddr 00:1a:70:13:8a:2a  
          inet6 addr: fe80::21a:70ff:fe13:8a2a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xde00 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:70:13:8a:2a  
          inet addr:169.254.4.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1072 (1.0 KB)  TX bytes:1072 (1.0 KB)

pan0      Link encap:Ethernet  HWaddr 72:f5:65:98:b3:f8  
          inet6 addr: fe80::70f5:65ff:fe98:b3f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:308143 (308.1 KB)

pan0:avahi Link encap:Ethernet  HWaddr 72:f5:65:98:b3:f8  
          inet addr:169.254.11.44  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

So, the reason this is so odd is that the output (as far as I can tell) is wrong. The mac address listed for 'eth1' is the same as the network card, but under the network connections it is listed as 'Wired Connection 1'. And I really have no idea what the other stuff is (with the exception of the 'lo'). In Newfoundlander's post, someone said that if the output of ifconfig was iffy, it might be a driver issue. If so, what driver is faulty? 

From what Newfoundlander said, I also tried inserting a the 9.04 live cd and both ports worked with that, so I am certain that this is a software issue with my installed version. Also, the wireless/wired internet for my linux laptop (running xubuntu) works fine, so it shouldn't be a router/linux discrepancy. 

So, I suppose my question(s) are/is: What does the seemingly incorrect output of 'ifconfig' mean, and if it is a driver issue, which driver do I need to re-install? If it is not the ifconfig stuff, what else might it be?

A few more tidbits of information which might help:
 - /etc/NetworkManager/nm-system-settings.conf was already altered for the '[ifupdown]/managed is set to true' thing a while ago.

Let me know if you would like to see output from anything else.

-Dillon

---

### Post by Iowan on 2009-07-26
A separate thread was a good idea - we can concentrate on your problem - which might be more hardware-related. 
Are both cards connected? I notice an IP address for eth0.
 eth1 may have tried/failed DHCP, and got avahi address (169.254.4.46). There may be a couple of "tricks" to get eth1 used (like setting up eth0 in */etc/network/interfaces* as "manual").

---

### Post by t0mppa on 2009-07-26
Without being an expert on troubleshooting wired connections, a few things caught my eye here.

Ifconfig shows that you're getting an IP, etc. through eth0. That means it has established at least a local network connection, packets have also been transmitted and received, so it has found something from the network, presumably the router. Without being able to browse internet, there are two simple things that you should check before starting to reinstall drivers: your gateway and DNS server.

Since the network manager claims you're connected, I'd guess it's the DNS that's giving trouble here. Try pinging 74.125.79.99 instead of the domain name ([www.google.com](www.google.com)) and see if it can reach by IP. If that works, you just need to check the DNS settings at /etc/resolv.conf

If you still can't reach the destination with the ping, then you can run **route** from the terminal and check if it gives a default route. That would be your gateway, through which all traffic going outside your local network has to go. If one isn't found your system won't know where to route all that traffic.

And about the "odd" ifconfig output:
[LIST]
[*]Avahi (see the quote) is enabled by default on Jaunty
[*]l0 is the local loopback
[*]pan0 is for bluetooth.
[/LIST]
[QUOTE=Wikipedia]Avahi is a free Zeroconf implementation, including a system for multicast DNS/DNS-SD service discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example, you can plug into a network and instantly find printers to print to, files to look at and people to talk to.[/QUOTE]

EDIT: Ah well, Iowan beat me to it, so guess you're safer listening to him.

---

### Post by drfoight on 2009-07-26
Thanks for the replies Iowan and t0mppa. I will address your questions/suggestions in order:

Iowan:
> Are both cards connected? I notice an IP address for eth0.
Yes. This was the first thing I checked (before connecting to the internet I did move the computer, so I thought it might have been bumped loose or something). Technically, eth0 isn't a card, because it is the ethernet port on the mother board. However, 'Wired Connection 1' (or eth1 as ifconfig identifies it), is an actual card, which responds in the same way as eth0 when plugged in.

> There may be a couple of "tricks" to get eth1 used (like setting up eth0 in /etc/network/interfaces as "manual").
I may need you to elaborate on this, or point me towards a thread that does, unless the answers to t0mmpa's suggestions trigger something.

t0mppa:
> Try pinging 74.125.79.99 instead of the domain name ([www.google.com](www.google.com)) and see if it can reach by IP. If that works, you just need to check the DNS settings at /etc/resolv.conf
So, I did this, and it worked! So, I checked the resolv.conf file, and this is what is contained:

```

domain Belkin
search Belkin
nameserver 192.168.2.1

```

I'm not sure what I should be looking for, but I don't see anything that looks outright wrong. My router is a Belkin, so the domain and search make sense (I think, again, I don't really know what is totally correct). The nameserver is slightly different than what has been suggested in other threads (like in Newfoundlander's thread someone suggested that the nameserver line be added with the address: 192.168.1.1), but I changed it to that and logged out and back in and nothing appeared to be changed. 

I ran the 'route' command as well, and this is what came out:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 pan0
link-local      *               255.255.0.0     U     0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 pan0
```

Again, I am not sure what it would look like if it was wrong, but nothing screams incorrect there. I switched the ethernet cable from the MB port to the network card and ran route again, and got the same thing with eth1 substituted for eth0.

So, hopefully that gives you guys some more ideas. Thanks for everything so far though. 

-Dillon

---

### Post by drfoight on 2009-07-27
bump for any new ideas?

---

### Post by martinbaselier on 2009-07-27
domain Belkin
search Belkin
nameserver 192.168.2.1 -> DNS server

ping [www.google.com](www.google.com) shows unknown host, but pinging the ip address directly works. 

This suggests a dns problem.
You can either add the dns servers from your provider to resolv.conf or use opendns.

To make this permanent, you would need to add a few line to /etc/dhcp3/dhclient.conf

I've added these lines to it (for open DNS)
append domain-name-servers 208.67.222.222;
append domain-name-servers 208.67.220.220;

This makes my resolv.conf look like this:
domain lan
search lan
nameserver 192.168.1.254
nameserver 208.67.220.220
nameserver 208.67.222.222

---

### Post by Iowan on 2009-07-27
> **t0mppa said:**
> EDIT: Ah well, Iowan beat me to it, so guess you're safer listening to him.It's not often that I have a quicker trigger...> **drfoight said:**
> 
I may need you to elaborate on this, or point me towards a thread that does, unless the answers to t0mmpa's suggestions trigger something.
Try adding a line to */etc/network/interfaces* like:```
iface eth0 inet manual
``` (Do NOT add the "auto eth0".) This *might* "tie up" eth0 and let eth1 get the address instead.  If it doesn't, you can comment out the line, delete it, or revert to the backup file you made before editing ;)

BTW, you will need to restart.

---

### Post by martinbaselier on 2009-07-27
no need to reboot.

Just restart networking:

sudo service networking restart

---

### Post by Iowan on 2009-07-27
Try it with just a networking restart... my machine needed a reboot to get Network Manager to take control of a different device.

(and **sudo reboot** was easier to type ;) )

---

### Post by Newfoundlander on 2009-07-27
Adding the Open DNS lines to my resolv.conf did not fix my problem.  Anyone else have any luck with it?

---

