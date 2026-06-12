---
title: "Hamachi problems, can connect but not ping"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by BCVisin on 2006-07-03
I have installed hamachi on plenty of fedora distros and it has wored fine.  I have been happy with it, but today I installed Ubuntu (YAY, not using windows anymore), but I can not seem to get it up and working.  I am able to connect to the hamachi server and see all of the computers on the network, but I can not conenct out.  I can't even ping any of the 5.x.x.x addresses.  I thought it was the iptables, so I flushed them, but still no...

Out of ideas, any help is much appreciated.

---

### Post by mrashley on 2007-01-29
I'm having the same problem.

I am using ghamachi on one (ubuntu 6.10) computer, and plain old hamachi on the other (ubuntu 6.06) computer. I am connected. They see eachother as online, but if I ping one another I get a respond from my local hamachi ip address saying Destination Host Unreachable.

I can ping my own hamachi ip address.

Thanks for any hints!

:D

---

### Post by mrashley on 2007-02-07
Seriously, has no one else had a similar problem?

---

### Post by andresgarcia on 2007-02-17
I have the same problem. I installed the ghamachi but I can not do ping and browse the devices that are on-line.

---

### Post by Bob Sugar on 2007-02-21
Ditto. Same problem.

Any answers yet?

---

### Post by mrashley on 2007-02-28
None here.  :(
*bump*

---

### Post by upekshapriya on 2007-02-28
I'm having the same problem with Xubuntu 6.06.1 LTS (which as been updated).

I did however find that it was working for about 5 minutes. I was fiddling and realised that I had installed it under root and wanted it under a user so I ran it again under a the user and it didn't work then - what I mean is that it will not connect over the network.

I have MacOS running hamachi and Windows XP - they can both see that the Xubuntu computer exists but it is greyed out and can't reach Xubuntu by pinging 5.x.x.x even though I can ping with 192.168.x.x!

On Xubuntu I can see the MacOS and WindowsXP 'connected' but I can't ping them either with 5.x.x.x but I can ping with 192.168.x.x.

On Xubuntu I can ping the 5.x.x.x. and 192.168.x.x and both work fine.

There seems to be something in Xubuntu stopping the connection. I don't have a firewall installed to my knowledge.

I'm glad I'm not the only one having the same problem. I can't find any solution on the hamachi forums or on here though. I have installed and deleted all the files I don't know how many times to no avail, thinking that some combination was wrong.

---

### Post by mrashley on 2007-03-24
Just goes to show sometimes it's best to put projects down and step away for a while. I fixed my problem - and hopefully this will help anyone else.

```
hamachi go-online <network name>

```

I was logged in and online, but somehow managed to missed this essential step. :P

Oh well - it's working now, hopefully this will help someone else.

---

### Post by Pettman on 2007-04-04
If you got firestarter installed, stopping the firewall helps. Can anyone help figuring out why it is that way and how to configure the firewall so you don't have to shut it down?

---

### Post by Xmister on 2007-05-19
I have the same problem, I'm in the room and I can see the other and they can see me as well, but I can't ping them. I get a 'destination host unreachable' message from ping.

Update:
I added this to /etc/network/interfaces:
(You can get your ips from ifconfig when hamachi is online (after hamachi start)
> iface ham0 inet static
address <your_ham0_ip>
netmask 255.0.0.0

iface ham1 inet static
address <your_ham1_ip>
netmask 255.0.0.0

auto ham0
auto ham1

And I don't know it's important but after i go-online to a room restarted the network with > sudo /etc/init.d/networking restart
And after that i can ping the others and they can ping me too.

---

### Post by perltom2004 on 2007-11-27
I had the same problem and fixed it by correcting the entry for hamachi virtual device in the routing table.

To check if the problem is caused by invalid routing entry do this: 
1) open the terminal
2) ifconfig
you should see something like this

ham0      Link encap:Ethernet  HWaddr 00:FF:CA:D0:F5:AA  
          **inet addr:5.23.68.35**  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:26780 (26.1 KB)  TX bytes:21076 (20.5 KB)

The IP address of the ham0 interface is the IP of the gateway for all hamachi network bound connections.

3) check the routing table with 
route -n
root@cronos:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
64.238.220.160  0.0.0.0         255.255.255.240 U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         5.23.68.35      255.0.0.0       UG    0      0        0 ham0
0.0.0.0         64.238.220.161  0.0.0.0         UG    100    0        0 eth0

The 3rd line defines hamachi connections.
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
5.0.0.0         5.23.68.35      255.0.0.0       UG    0      0        0 ham0

If in the Gateway column you don't see the IP of the ham0 interface, as it was the case with me, delete that line and create the correct routing entry for hamachi.

delete invalid route:
route del -net 5.0.0.0 gw 0.0.0.0 netmask  255.0.0.0 dev ham0

add new route:
route add -net 5.0.0.0 gw 5.23.68.35 netmask  255.0.0.0 dev ham0

This should fix the ping problem. I hope it helped.

good luck,

Dimitar



If you have successfully installed hamachi and have problems pinging your hamachi network then most probably you need to check the routing table.

---

### Post by perltom2004 on 2007-11-27
Hi,

have to correct myself 

I repeated the steps and the routing table was ok. Simple hamachi go-online <network> *corrected* the ping and connectivity problem.

I am new with Hamachi 

dimitar

---

### Post by bjolle on 2007-11-30
> **perltom2004 said:**
> 

(...)

delete invalid route:
route del -net 5.0.0.0 gw 0.0.0.0 netmask  255.0.0.0 dev ham0

add new route:
route add -net 5.0.0.0 gw 5.23.68.35 netmask  255.0.0.0 dev ham0

(...)




This doesn't look right. Hamachi is a virtual ***LAN***, which means that no gateways should be involved. And why would you use your own local interface as a gateway anyway?

B

---

### Post by thelorax on 2008-01-06
> **Xmister said:**
> I have the same problem, I'm in the room and I can see the other and they can see me as well, but I can't ping them. I get a 'destination host unreachable' message from ping.

Update:
I added this to /etc/network/interfaces:
(You can get your ips from ifconfig when hamachi is online (after hamachi start)

And I don't know it's important but after i go-online to a room restarted the network with 
And after that i can ping the others and they can ping me too.


Xmister's tip worked for me too (Ubuntu 7.04 & hamachi-0.9.9.9-20-lnx-pentium) I could log-in with Hamachi and see other computers (and they could see me) but I couldn't ping or otherwise connect over the vpn.  I updated my /etc/network/interfaces, restarted the networking and it worked like a charm!

---

### Post by Ryan Marcus on 2008-05-06
Xmister! You are my new personal hero! You've replaced Bono, at least until he saves some more Africans.

That solution worked for me. Here is my /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto ham0
iface ham0 inet static
address ** hamachi ip *
netmask 255.0.0.0

```

To get your Hamachi IP, go online with Hamachi and type:

ifconfig | grep :5. | grep inet

Ya, it is a little hackish, but it works.

```

ryan@ryan-desktop:~/Desktop/hamachi-0.9.9.9-20-lnx$ ifconfig | grep :5. | grep inet
inet addr:**5.210.118.121**  Bcast:5.255.255.255  Mask:255.0.0.0


```

---

### Post by elrossco22 on 2008-06-01
hi i installed himachi on my computer and the minute i started it up it made its own internet connection in my availible networks after this i tried connecting to the real interner via my wireless but couldnt i was getting the signal but my browser was not using it.i then uninstalled himachi and disscovered it had took my internet protocol settings and networks settings with it i now have no internet and have no known way off fixing it i have to use a friends computer to write this to find out a solution to my problem.the version of hamachi i downloaded was from a website which i cannot remember.

[SIZE="6"]please help me[/SIZE]

---

### Post by Rackham on 2008-06-01
Hamachi creates a secondary connection that it uses as a "tunnel" through which it passes secure traffic. It essentially works along side your current connection, but shouldn't modify your other settings. 

My guess is that you accidentally modified your network settings to use Hamachi as the primary with which to connect to the internet - you'll need to go into your network settings to designate the original connection as the primary.

Most of my experience with Hamachi is Windows based, since I only have Ubuntu installed as a learning system. Maybe someone with a little more experience will chime in and give you a better answer.

---

### Post by britline on 2008-07-03
/etc/init.d/ipmasq restart, if you have router with masqurading configuration... maybe help...

---

