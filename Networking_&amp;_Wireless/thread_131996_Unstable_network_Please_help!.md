---
title: "Unstable network: Please help!"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by jpradel on 2006-02-17
I'm using Ubuntu since a year but, recently I started having problems with networking.
Configurations:
- Acer TravelMate 3002WTMi
- Wireless card (included, don't know more)
- ADSL / wireless router
Simptoms:
- Router working perfectly well with Windows
- In Ubuntu, network working for local addresses (other computers in the local network, the printer, etc.)
- Network only occasionally working for Internet addresses. i. e. A ping to [www.google.com](www.google.com) works only now and then with high packet loss %.
Details:
- sudo ifconfig:
sudo ifconfig:
eth1
  Link encap:Ethernet  HWaddr 00:13:CE:27:7C:CD
  inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
  inet6 addr: fe80::213:ceff:fe27:7ccd/64 Scope:Link
  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  RX packets:21976 errors:0 dropped:20 overruns:0 frame:0
  TX packets:21402 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:1000
  RX bytes:8574056 (8.1 MiB)  TX bytes:1510720 (1.4 MiB)
  Interrupt:10 Base address:0xa000 Memory:b0118000-b0118fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3736 (3.6 KiB)  TX bytes:3736 (3.6 KiB)

sudo route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

I have no idea what's going wrong. Please, help!

Jordi
- Help me Obi Wan Kenobi. You are my last hope.

---

### Post by bscbrit on 2006-02-18
When you can ping numbered connections (192.168.0.2) but not named sites ([www.google.com](www.google.com)) it is usually a sign that your DNS is not configured properly.  Please post the contents of your /etc/hosts file.  Are you using NetworkManager (which overwrites your DNS configuration)?

---

### Post by jpradel on 2006-02-18
First of all, thanks for your fast answer.

I'm using network-admin config tool, so, I suppose I'm using NetworkManager.

But it seems not a DNS problem, since I have the same problem with IP addresses. When I do a ping, it takes more than 30 seconds to output the first line. Then, it starts working more or less well.

I made a tracepath [www.google.com](www.google.com) and obtained:
1: 192.168.1.66 (192.168.1.66)       0.112ms pmtu 1500
--> And after a few seconds:
1: 192.168.1.1 (192.168.1.1)       asymm 101 1.937ms
2: no reply
3: no reply
4: no reply
...

My /etc/hosts:
127.0.0.1 localhost.localdomain localhost portatil-jordi
192.168.1.50 oracle

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Notes:
- In network-admin tool I use:
  - Static IP: 192.168.1.66
  - Network submask: 255.255.255.0
  - Default gateway: 192.168.1.1 (my router)
  - hostname: portatil-jordi
  - domain name blank (not filled)
  - DNS servers: Same I use on a Windows box that's working
  - Search domains: localhost.localdomain

Hope this helps to help and, thanks again.
Jordi

---

### Post by bscbrit on 2006-02-18
It sounds like you are not configured for any DNS outside of your own network.  The contents of /etc/resolv.conf are now needed to see how your machine is resolving names.
NetworkManager is _not_ the same as the network configuration GUI.  It is a separate program that is installed to support the move between wireless/wireless and wireless/wired networks.  But, in so doing, it rewrites several configuration files on your computer which can interfere with other network settings.  The fact that you have a wireless card made me think of it.
Can you ping your own NIC and your router from the commandline?  And 'oracle', whatever that is?

---

### Post by jpradel on 2006-02-18
Ok, here we go:
/etc/resolv.conf:
nameserver 62.36.225.150
nameserver 62.37.237.140

Those are the name servers I manually configured.

Oracle is a server in my own network (wich serves an Oracle DB, hence de name). I can ping without problems oracle, 192.168.1.1 and any other host in my local network. But ping behaves awkward against external hosts, EVEN using IP adresses (ping [www.google.com](www.google.com) and ping 66.102.9.147 do the same). I think my DNS are correctly configured, but I have trouble reaching external hostst. This includes my DNSs.

I don't know what my NIC is (sorry about my newbyness).

Interesting note:
- I've tested to connect through my wired network (eth0 in my case) and it works perfectly well with same IP/DNS configs.
- My wireless network works well within my LAN. I suppose it has something badly configured.

Thanks again. Hope we are advancing to a soluition. I love wireless connectivity.

Jordi

---

### Post by bscbrit on 2006-02-18
Good - lots of useful information there.  As you say, your DNS is configured correctly and is working.  The most useful piece of information is that your wired network works faultlessly, but your wireless network has problems which indicates, as you also know, that this is a wireless specific problem.

Your NIC is your network interface card, but you have already shown that it is working by the previous tests.

But you mentioned that you switched over to your wired network - using which settings? I suspect the problem (or at least a clue to the answer) now lies in the one file we haven't yet looked at - /etc/network/interfaces.  This file is responsible for setting up both the wired and wireless networks and so is prime candidate for the problems you are experiencing.  Please show the contents of your interfaces file.

---

### Post by bscbrit on 2006-02-18
While I'm waiting for your interfaces file (which I need in order to answer a query that I have), I'll let you know what I'm thinking.

On your computer, you have eth1 configured as 192.168.1.37, but in the network gui you mentioned that you have set 192.168.1.66.  They can't both be right, hence I would like to look at your interfaces file.

Secondly, you have mentioned both a wired and a wireless network.  Well only one of them appears to be configured and I need to work out which one it is (yep, interfaces file again).

Thirdly, you cannot have _both_ configured and working at the same time.  They can both be configured but only one of them can be your preferred route to the outside world.

The problem could be in either the wireless NIC configuration or in your wireless router.  But you also mentioned that your wired network is fine - do they both use the same ADSL modem/router and, if so, I assume that it has both wireless and cable network connections?
EDIT: And as your wireless network is OK locally, it points to a problem in the router configuration rather than the NIC.  What make and model is it, and do you configure it using a browser, telnet or mystic incantations?

So, once I have the details of your file, I can try to work out what is, and what is not, configured. :-D

---

### Post by jpradel on 2006-02-18
Sorry, I made a mistake. I switched to DHCP to see if my static config was the problem, but it wasn't. So I tested both static IP 192.168.1.66 and DHCP (which gave me 192.168.1.37 you saw). I mess IPs up when I wrote last message.

I have 2 network (eth0 -> wired network, eth1 -> wireless one). I have the problems when eth1 activated but eht1 not. I switch eht0 and eth1 on and off from network-admin tool. So I'm not trying with both connections up, because I suppose that would be messy and not necessary. In any case, I tested both with dhcp and only the wired (cable) connections works.

Both connections use the same router (which is wireless and wired).

When using DHCP and activating only eth1 (wireless connection), I still have the same problems. My /etc/network/interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo

iface lo inet loopback
        address 127.0.0.1
        netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
# hostname 192.168.1.1
# wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid <myessid>
        wireless-key <mykey>

iface eth0 inet dhcp

Since I have no idea what the wireless NIC configuration is, I suppose that's is the problem. :mrgreen:

cu,
Jordi

---

### Post by bscbrit on 2006-02-18
Right - i think I understand what you are trying to tell me.....:p 

First of all, here is a copy of part of my interfaces file:

iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid bscbritnet
wireless-nick spare
wireless-channel 6
wireless-mode managed
wireless-ap 00:13:46:9E:FF:FF
wireless-key1 aa11bb22cc33dd44ee55ff6600
wireless-defaultkey 1
wireless-keymode open


Yours will differ of course.  You are using dhcp where I am using static, and so you will not need the next line which allocates a static address.  But you _will_ need the line which tells your wireless how to reach the internet.  So, in your case, 'gateway 192.168.1.1'.  I also told my wireless card which channel to use - because I get interference from other local wireless networks.  In fact, I had to specify the wireless-ap address to avoid some problems - not quite sure why because it shouldn't be necessary, but it works.

You could also run the following command:

sudo iwlist scan

This should show you how many wireless networks your card can 'see' - if you don't get at least one you have a major problem ( :D ) but you may find more, it rather depends on your environment.  Anyway, try the settings suggested above, restart your network (sudo /etc/init.d/networking restart) and see if that helps.  Also provide the details of your modem/router please.

---

