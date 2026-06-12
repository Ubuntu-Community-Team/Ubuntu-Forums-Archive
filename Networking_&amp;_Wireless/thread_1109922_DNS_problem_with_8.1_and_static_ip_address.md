---
title: "DNS problem with 8.1 and static ip address"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by neilg4rqn on 2009-03-29
Hello. For reasons that are unimportant here I want to have a static ip address on my ubuntu box. Using my windoze box I found some advice that said I should remove the Network Manager which I have done, and remove dhcp3-client (think that's right) which I have also done. Now I cannot get the DNS side of things to work so I cannot access any web sites by name, not even my Apache stuff that I started to play with "http//localhost", it worked OK until I started to try to get the static ip address working. I can access Google etc if I enter the ip address [http://209.85.227.147/](http://209.85.227.147/) so I have web access of a sort. I am using Ubuntu 8.1 32 bit on a small home network with a router so all fairly normal.
Here is the putput from ifconfig
```

eth0 Link encap:Ethernet HWaddr 00:0f:ea:ee:69:23
inet addr:192.168.0.11
Bcast:192.168.0.255  
Mask:255.255.255.0
inet6 addr: fe80::20f:eaff:feee:6923/64 Scope:Link           
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           
RX packets:401 errors:0 dropped:0 overruns:0 frame:0           
TX packets:216 errors:0 dropped:0 overruns:0 carrier:0           
collisions:0 txqueuelen:1000            
RX bytes:80428 (80.4 KB)  TX bytes:55531 (55.5 KB)           
Interrupt:18 Base address:0xc400

lo Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:696 errors:0 dropped:0 overruns:0 frame:0
TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:60270 (60.2 KB)  TX bytes:60270 (60.2 KB)

```
Here is the output from /etc/network/interfaces
```

# The loopback interface 
auto lo iface lo inet loopback 
# The primary interface interface static 
auto eth0 
iface eth0 inet static 
address 192.168.0.11 
netmask 255.255.255.0 
network 192.168.0.0 
broadcast 192.168.0.255 
gateway 192.168.0.1

```
and the output from /etc/resolv.conf
```

nameserve 212.159.13.49 
nameserve 212.159.13.50 
nameserve 212.159.6.10

```
Any ideas gratefully received !
Neil R :confused:

---

### Post by chili555 on 2009-03-29
> nameserveDo you really mean *nameserve**r***?

---

### Post by pbpersson on 2009-03-29
1. The Ubuntu version number is 8.10 not 8.1 - it was released in 2008-October which is why the "10" part is there

2. I don't know why you were told to REMOVE packages from the machine to setup a static IP address, I would have gone into the network settings and just SET it to static, just like in Windows.  Do you think one of those missing packages could be the cause of your problems?

---

### Post by neilg4rqn on 2009-03-29
Em yes that's what the instruction read

---

### Post by neilg4rqn on 2009-03-29
Part of what I read said that due to a bug in 8.10 (thanks for correction) if you leave them in all the static stuff gets overwritten.

---

### Post by pbpersson on 2009-03-29
What happens when you go to a command line and type the following:

```
nslookup www.google.com
```

---

### Post by neilg4rqn on 2009-03-29
> **pbpersson said:**
> What happens when you go to a command line and type the following:

```
nslookup www.google.com
```

;; connection timed out; no servers could be reached

---

### Post by pbpersson on 2009-03-29
> **neilg4rqn said:**
> 
and the output from /etc/resolv.conf
```

nameserve 212.159.13.49 
nameserve 212.159.13.50 
nameserve 212.159.6.10

```
Any ideas gratefully received !


This is going to sound dumb, but I just looked in my resolv.conf and it says **nameserver** in mine.  Can you go in there, manually change it, and then see what happens?  If it still does not work, try a reboot.

I was just reading another article, you can restart the networking components without rebooting by using the following command:

```
sudo /etc/init.d/networking restart
```

---

### Post by neilg4rqn on 2009-03-29
> **pbpersson said:**
> This is going to sound dumb, but I just looked in my resolv.conf and it says **nameserver** in mine.  Can you go in there, manually change it, and then see what happens?  If it still does not work, try a reboot.

I was just reading another article, you can restart the networking components without rebooting by using the following command:

```
sudo /etc/init.d/networking restart
```

Why is it that the best errors never become obvious until someone else walks up behind you and says "it's obvious, look what you have put there". Now I feel a right d*** head :lolflag:
many thanks pbperson
Long live ubuntu

---

### Post by pbpersson on 2009-03-29
I am just glad it was an easy fix \\:D/

---

### Post by neilg4rqn on 2009-03-29
> **chili555 said:**
> Do you really mean *nameserve**r***?

Sorry friend but I didn't even then notice that you told me first ! Perhaps my kids are right ....

---

### Post by chili555 on 2009-03-29
Perhaps I should have been clearer and asked you at the outset to change the file. I wondered, however, if you just made an error posting it in the forum and if it was, indeed, correct in the actual file.

---

### Post by neilg4rqn on 2009-03-29
So near yet so far. great I thought - now I can get on the web etc. Well nearly - I cannot yet get to [http://localhost](http://localhost)

---

### Post by DGortze380 on 2009-03-29
> **neilg4rqn said:**
> So near yet so far. great I thought - now I can get on the web etc. Well nearly - I cannot yet get to [http://localhost](http://localhost)

can you please post the output of 

```

cat /etc/hosts

```

look for the line

```

127.0.0.1          localhost

```

add it at the top of the file if it doesn't exist.

---

### Post by neilg4rqn on 2009-03-29
Hi Dgortze380, here it is

neil@neil-ubuntu3:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	neil-ubuntu3

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by casdio on 2009-03-29
Hi.
Sorry for post it here, but I think it's on-topic.

My /etc/resolv.conf file changes himself. I asked a friend to let me see his file and it said:
> #Generated by network manager

Mine says:
> # Dynamic resolv.conf( 5) file for glibc resolver( 3) generated by resolvconf(8 )
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

Anyone knows what the problem can be? I don't want it to change alone :|

---

### Post by DGortze380 on 2009-03-29
> **casdio said:**
> Hi.
Sorry for post it here, but I think it's on-topic.

My /etc/resolv.conf file changes himself. I asked a friend to let me see his file and it said:


Mine says:


Anyone knows what the problem can be? I don't want it to change alone :|

Please start your own thread for this problem

---

### Post by DGortze380 on 2009-03-29
> **neilg4rqn said:**
> Hi Dgortze380, here it is

neil@neil-ubuntu3:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	neil-ubuntu3

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

weird, what happens if you ping localhost?

---

### Post by neilg4rqn on 2009-03-29
I was told that the network manager would overwrite that file and the advice I had was to remove it, bet to read all of this thread first though.

---

### Post by neilg4rqn on 2009-03-29
Hi, yoou wrote "weird, what happens if you ping localhost?"

neil@neil-ubuntu3:~$ ping [http://localhost](http://localhost)
ping: unknown host [http://localhost](http://localhost)

then I tried

neil@neil-ubuntu3:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.043 ms

and I get a reply. When I type localhost into my browser it adds the http:// bit.

---

### Post by DGortze380 on 2009-03-29
> **neilg4rqn said:**
> Hi, yoou wrote "weird, what happens if you ping localhost?"

neil@neil-ubuntu3:~$ ping [http://localhost](http://localhost)
ping: unknown host [http://localhost](http://localhost)

then I tried

neil@neil-ubuntu3:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.043 ms

and I get a reply. When I type localhost into my browser it adds the http:// bit.

Not a resolution problem. Check your apache configs.

---

### Post by neilg4rqn on 2009-03-29
Many thanks for that. It's kinda late now so I will follow your suggestion during the week.

---

