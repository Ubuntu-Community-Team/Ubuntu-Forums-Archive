---
title: "Access to router but not internet"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-02-03
I've been working on geting my box to have a static ip.
I have the address set and now i can access my router, but I cannot access the internet. IF i switch to wireless i get internet.

I set up port forwarding. 

21 and 80 to my box, but still nothing?

Linksys router.

---

### Post by Kebabman on 2009-02-03
What happens when you go to a terminal and type :

ping 74.125.77.103

Paste the output in here

---

### Post by kbutcher5 on 2009-02-03
> **Kebabman said:**
> What happens when you go to a terminal and type :

ping 74.125.77.103

Paste the output in here
I root for a possible DNS issue aswell, do as the man says! :)

---

### Post by wlraider70 on 2009-02-03
From my box with the trouble...

if i have wirless on (thats the DHCP to the router)

luke@ubuntu:~$ ping 74.125.77.103
PING 74.125.77.103 (74.125.77.103) 56(84) bytes of data.
64 bytes from 74.125.77.103: icmp_seq=16 ttl=240 time=170 ms

64 bytes from 74.125.77.103: icmp_seq=17 ttl=240 time=203 ms
64 bytes from 74.125.77.103: icmp_seq=18 ttl=240 time=188 ms
64 bytes from 74.125.77.103: icmp_seq=19 ttl=240 time=170 ms
64 bytes from 74.125.77.103: icmp_seq=20 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=21 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=22 ttl=240 time=172 ms
64 bytes from 74.125.77.103: icmp_seq=23 ttl=240 time=170 ms
^C
--- 74.125.77.103 ping statistics ---
23 packets transmitted, 8 received, 65% packet loss, time 22037ms
rtt min/avg/max/mdev = 167.489/176.584/203.367/11.752 ms
luke@ubuntu:~$ 




IF i use the wired, that the one i'm trying to get to Static i get


luke@ubuntu:~$ ping 74.125.77.103
PING 74.125.77.103 (74.125.77.103) 56(84) bytes of data.
64 bytes from 74.125.77.103: icmp_seq=1 ttl=240 time=168 ms
64 bytes from 74.125.77.103: icmp_seq=2 ttl=240 time=168 ms
64 bytes from 74.125.77.103: icmp_seq=3 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=4 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=5 ttl=240 time=168 ms
64 bytes from 74.125.77.103: icmp_seq=6 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=7 ttl=240 time=170 ms
64 bytes from 74.125.77.103: icmp_seq=8 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=9 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=10 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=11 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=12 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=13 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=14 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=15 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=16 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=17 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=18 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=19 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=20 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=21 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=22 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=23 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=24 ttl=240 time=197 ms
64 bytes from 74.125.77.103: icmp_seq=25 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=26 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=27 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=28 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=29 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=30 ttl=240 time=167 ms
64 bytes from 74.125.77.103: icmp_seq=31 ttl=240 time=168 ms
64 bytes from 74.125.77.103: icmp_seq=32 ttl=240 time=173 ms
64 bytes from 74.125.77.103: icmp_seq=33 ttl=240 time=169 ms
64 bytes from 74.125.77.103: icmp_seq=34 ttl=240 time=170 ms
64 bytes from 74.125.77.103: icmp_seq=35 ttl=240 time=204 ms
64 bytes from 74.125.77.103: icmp_seq=36 ttl=240 time=168 ms

---

### Post by Kebabman on 2009-02-03
So you have access to the Internet then, you are just not able to resolve DNS names. Have you set a DNS server address in /etc/resolv.conf, or in network-admin ?

---

### Post by wlraider70 on 2009-02-03
No I didn't how would i do that?

my file looks like this 


...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface , all the 3rd level "1" were "0"
auto eth0
iface eth0 inet static

address 192.168.1.120
netmask 255.255.255.0
broadcast 192.168.1.255
gateway  192.168.1.1


....

---

### Post by Kebabman on 2009-02-03
You need to include a stanza in /etc/network/interfaces to tell it what ip address to use for DNS lookups, this will either be your router IP or the address of a DNS server supplies to you by your ISP. The stanza looks like this :

dns-nameservers 195.238.2.21 195.238.2.22

It might just have one address if it is your router IP.

It should go somewhere under the 'iface eth0 inet static' line

---

### Post by wlraider70 on 2009-02-03
ok my file now looks like this...

iface eth0 inet static

address 192.168.1.120
netmask 255.255.255.0
broadcast 192.168.1.255
gateway  192.168.1.1
dns-nameservers 67.138.54.100 192.168.1.1

....

The first is a free DNS since i dint want to stop and go look for the isp address, the second is my router.

Neither seem to work.

DO i have to reboot or do anything to get the changes in the file to "update"?

---

### Post by Kebabman on 2009-02-03
type the following in a terminal to restart the networking using those settings :

sudo /etc/init.d/networking restart

That should reload it all for you

---

### Post by wlraider70 on 2009-02-03
Ok, I'm taking a break cuz this is making me mad but i have an idea.

the    /etc/resolv.conf file

tells me that my DNS is generated my network manager and that it is "10.10.10.2"  that is the address of the main server.

The Linux sever i am trying to set up is in the school computer lab, it connects to a router, the router gets its internet from the main windows server.


DSL modem -> to switch 1 -> Windows main network (lpcc)
Switch 1-> to linksys router 2 -> Linux server (lpcs)



I am not trying to extend the network just barrow the internet connection. I didn't think this would be an issue but it looks like it might be. Also The linksys router 2 is recognizing that it is connected to 10.10.10.2 as its DNS. When I go wireless DHCP the router resolves just fine. It is only my attempt to make a static wired connection for the Linux server that seems to fail.

I hope that makes some sense.

---

### Post by wlraider70 on 2009-02-03
I think my /etc/resolv.conf file is over riding my /etc/network/interfaces.

The resolve file keeps changing itself to a DNS that i don't think my Linux box can access. The interfaces has been set to MANY working DNS. I think whenever i restart the network manager either my reboot or code. it defaults back and get overridden.

---

### Post by Iowan on 2009-02-03
[Here]("http://ubuntuforums.org/showthread.php?t=971064") is a thread about nameserver issues.

---

### Post by wlraider70 on 2009-02-05
The work around leads to the same site as the guide.

---

