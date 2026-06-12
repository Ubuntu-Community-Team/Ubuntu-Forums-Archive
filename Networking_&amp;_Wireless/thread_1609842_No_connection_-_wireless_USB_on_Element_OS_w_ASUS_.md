---
title: "No connection - wireless USB on Element OS w/ ASUS N13"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by sctechlaw on 2010-10-30
I need some assistance please. I've read through this forum and found very helpful advice, followed it, and still can't connect, but think I'm getting close. Perhaps someone here could help. The problem as described is happening on an Element OS box (Ubuntu-based HTPC).

Topology:

..  cable modem > firewall/router > wireless AP > Element OS box > ASUS USB N-13 wireless adaptor

Network:

1. a dozen or so Windows boxes of varying flavors, an old Mac, an Ubuntu Maverick 10.10 box, a Pupply Linux box, and an Element OS box -- the one in question. 

2. The IP addressing is static and I need it to stay that way.

3. MAC address filtering on both the AP and the firewall/router.

What worked but is not optimal:

 .. as long as my AP (WPA2/AES) was broadcasting its ESSID, even NetworkManager could handle the static IP and I could connect just fine. But I don't want it broadcasting (yes even though anyone with a scanner can see hidden ESSIDs).

What I've tried so far:

Following advice given in other threads for installing the RT3070sta / RT2870sta, that worked to the extent I could then see my card. I found the thread by RedSultan (#1419504) to be of great help.

Eventually realizing that NetworkManager might have been part of the problem with static IPs and hidden ESSIDs, I uninstalled NetworkManager. I also uninstalled the Avahi daemon and its autoIPD. Before installing wicd I took the next steps:

Following the advice in the "Static IP" threads to edit my /etc/network/interfaces file, that worked to the extent that I was able to successfully configure the interfaces, after which I could see in iwconfig that my wireless USB card was not only using the right driver, but was connected to the AP (the one with the hidden ESSID). I found the thread #1176169 to be of great help too. 

Also, ifconfig shows my interfaces are up.

I made sure to stop and restart the network and to reboot between changes. 

I tried pinging the other nodes on the lan with success - all live nodes on the lan responded to my pings. The firewall/router also responded to my pings. So it does appear all lan nodes see each other, and that the MAC address filters are working correctly since otherwise I'd get no response at all from either the AP or the router.

The problem is, I can't get any further. After installing wicd, that app shows me as connected to my AP successfully, but any pings beyond the firewall/router to whatever dot com, fail with timeouts. My Ethernet connection works flawlessly. The firewall is a Netgear FVS338.

So, would someone please assist me in figuring out what I've missed? Thanks so much in advance.

---

### Post by chili555 on 2010-10-30
Have you set up DNS nameservers in /etc/resolv.conf?

---

### Post by sctechlaw on 2010-10-30
> **chili555 said:**
> Have you set up DNS nameservers in /etc/resolv.conf?
Yes, there are two lines there, one line for domain, and another for nameserver. Both appear correct, and are set to the router address as it handles things from there for my other machines.

---

### Post by chili555 on 2010-10-31
How about letting us have a look at:```
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```Thanks.

---

### Post by sctechlaw on 2010-10-31
> **chili555 said:**
> How about letting us have a look at:```
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```Thanks.
Hello Chili555 -- (is the 555 for the 5-alarm style chili? <smile>)
I made the route commands while the ethernet cable was unplugged. ```
jupiter@solarsys:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
jupiter@solarsys:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 ra0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
jupiter@solarsys:~$ sudo cat /etc/resolv.conf
[sudo] password for jupiter: 
domain 192.168.1.1
nameserver 192.168.1.1

jupiter@solarsys:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

# wired ethernet
auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
nameserver 192.168.1.1

# wireless rt2870sta
auto ra0
iface ra0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
nameserver 192.168.1.1
wpa-driver wext
wpa-ssid none
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <passphrase removed for post>
```Thanks

---

### Post by chili555 on 2010-10-31
Why do you want or need both wired and wireless connected at the same time? In /etc/network/interfaces, when you preface the  interface with 'auto,' that's what you are asking for. 

Please detach the ethernet cable and reboot. Then do:```
ping -c3 192.168.1.1
ping -c3 74.125.65.100
ping -c3 www.google.com
```Then amend your /etc/resolv.conf to read as follows:> [COLOR="Red"]#[/COLOR]domain 192.168.1.1
nameserver 192.168.1.1Then try:```
ping -c3 www.google.com
```It is very hard to diagnose problems with wireless when the wired ethernet is connected. Ping results, for example, are meaningless.

---

### Post by sctechlaw on 2010-10-31
> **chili555 said:**
> Why do you want or need ...
I appreciate your assistance chili555. I only had the ethernet cable attached in order to connect and answer your query, as I can't yet connect via wireless. All terminal commands I made for the prior post were with the box booted with ethernet cable unplugged.

As I am pretty new to Ubuntu, I don't know the purpose of the "auto" in the interfaces file. In the eth0 portion of the interfaces file, I have now commented out the first line, so:
#auto eth0

I rebooted and pinged my router as you asked and it responded in kind with no packet loss. I then pinged google's IP and it timed out with 100% packet loss. 

I then amended the /etc/resolv.conf file as per your instruction above and tried pinging google but same result: 100% packet loss.

I am, however, able to send a test page to my printer on the same subnet and ping all other connection n the lan successfully.

---

### Post by chili555 on 2010-10-31
What do the other boxes have for DNS nameservers?```
ipconfig /a
```

---

### Post by sctechlaw on 2010-10-31
All the other boxes have the router (192.168.1.1) as both gateway and dns server. No other lan client, wired or wireless, including the other Ubuntu box and the Puppy Linux box, has a problem connecting. Those two 'nix boxes are wired, not wireless.

I thought it might be a firewall/router issue at first, but since I could connect wirelessly using NetworkManager, as long as I had a visible ESSID on the AP, (with the gateway and dns server address as 192.168.1.1), I'm thinking its not a router problem. I triple-checked my MAC address filters in the firewalls on the router and the AP, and they are correct. 

I am stumped, and grateful for any help.

---

### Post by chili555 on 2010-10-31
Did both Google by name *and* by number time out? May we see:```
traceroute www.google.com
cat /etc/hosts
```I am starting to get stumped myself and I don't stump easily!

---

### Post by sctechlaw on 2010-10-31
```
jupiter@solarsys:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.65 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.56 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.569/1.641/1.702/0.064 ms
jupiter@solarsys:~$ ping -c3 www.google.com
PING www.l.google.com (72.14.213.103) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms

jupiter@solarsys:~$ ping -c3 72.14.213.106
PING 72.14.213.106 (72.14.213.106) 56(84) bytes of data.

--- 72.14.213.106 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

``````
jupiter@solarsys:~$ traceroute www.google.com
traceroute to www.google.com (72.14.213.105), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  2.391 ms  2.695 ms  2.929 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
jupiter@solarsys:~$ sudo cat /etc/hosts
[sudo] password for jupiter: 
127.0.0.1    localhost
127.0.0.1    solarsys

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
jupiter@solarsys:~$ 

```

---

### Post by chili555 on 2010-10-31
> $ sudo cat /etc/hosts
[sudo] password for jupiter: 
127.0.0.1    localhost
[COLOR="Red"]127.0.0.1[/COLOR]    solarsys

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
Would you please amend this one line only to:```
127.0.1.1 solarsys
```All the rest of the file remains as is. Next restart networking:```
sudo /etc/init.d/networking restart
```And post back to tell me if there is any improvement.

---

### Post by chili555 on 2010-10-31
Please see Section 10.4 here: [http://qref.sourceforge.net/quick/ch-gateway.en.html](http://qref.sourceforge.net/quick/ch-gateway.en.html)> Most often this is done by putting a line in /etc/hosts containing some IP address and the system hostname. If your system has a permanent IP address then use that; otherwise use the address 127.0.1.1.

        127.0.0.1 localhost
        127.0.1.1 uranus

To see whether your system hostname can be resolved to an IP address with a fully qualified domain name, use the hostname --fqdn command. 

---

### Post by sctechlaw on 2010-10-31
Changed the localhost address as instructed to 127.0.1.1, and below follows what took place after the restart. The network restart took a very long time, after which I still couldn't connect, so then I rebooted. (The trick-or-treater's kept me busy while I was waiting for the reboot!) Tried to connect and, nothing.

You can see from the iwconfig result that my connection appears to be up and running, though it won't venture beyond the router.```
jupiter@solarsys:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"none"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:16:B6:4F:5E:9E   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-55 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jupiter@solarsys:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.20 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.47 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.86 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.39 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.98 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1.49 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=19.7 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.55 ms
^Z
[1]+  Stopped                 ping 192.168.1.1
jupiter@solarsys:~$ ping www.yahoo.com -c3
PING any-fp.wa1.b.yahoo.com (72.30.2.43) 56(84) bytes of data.

--- any-fp.wa1.b.yahoo.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2013ms

jupiter@solarsys:~$ ping -c3 72.30.2.43
PING 72.30.2.43 (72.30.2.43) 56(84) bytes of data.

--- 72.30.2.43 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms
```I'm starting to wonder if maybe I should uninstall the connector and begin from the beginning. Other thoughts?

---

### Post by chili555 on 2010-11-01
I wonder if this is a firewall issue. I am not familiar with Element, but in Ubuntu Gnome, I'd go to System > Administration > Firewall Configuration and see the attached. Make sure you are set as Allow:Allow or, for testing purposes, the firewall is turned off.

Next, I'd check to be certain there is no IP address conflict with another box on the network. I wonder if the router is sending return traffic to the *other* 192.168.1.2.

...stumped in SC!

---

