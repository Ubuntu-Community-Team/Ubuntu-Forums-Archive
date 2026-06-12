---
title: "IPV6 tunneling..."
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by superdupont on 2009-10-19
Hi.
I requested an ipv6 tunnel here :
[http://tunnelbroker.net/](http://tunnelbroker.net/)
in order to get ipv6 access on my Jaunty 64 bits.

all good they created it :
    Description:     
>[INDENT]>     Server IPv4 address:     216.66.xx.xx
>     Server IPv6 address:     2001:470.xxx.xx::1/64
>     Client IPv4 address:     90.3x.xxx.xxx 
>     Client IPv6 address:     2001:470.xxx.xx::2/64

[/INDENT][INDENT]>     Anycasted IPv6 Caching Nameserver:     2001:470:20::2
> 
>     Anycasted IPv4 Caching Nameserver:     74.82.42.42
> ---------------------------------------------------------------------
[/INDENT]---[INDENT]>     Routed /48:     _Allocate_
>     Routed /64:     2001:470.xxx.xx::/64[/INDENT]problem is, tunnelbroker does provide some configuration samples for various systems, but nothing for ubuntu/debian, and I don't know much about networking.

from what I read, I have to update things in etc/network/interfaces and maybe add some route, so if someone could help here with the required lines/commands on ubuntu... :)
thanks in advance

---

### Post by Wordan on 2009-10-19
I set up an ipv6 tunnel recently from tunnelbroker.net. I found the route2 command example worked fine. It will let you access ipv6 from the machine you have the tunnel set up on.

If you want to make ipv6 available on your LAN you would have to do the following:

1. Enable ipv6 forwarding on the machine you have the tunnel set up on to allow it to act as a router.

2. Install radvd(router advertising deamon) and set it up to advertise the Routed /64 subnet you've been given by the tunnel broker. This allows stateless autoconfiguration of ipv6 addresses on your LAN on hosts that have ipv6 support.

3. Create an ipv6 route for packets destined for your Routed /64 subnet so they are forwarded from your tunnel interface to the networkcard connected to your LAN

4. Create an ipv6 route to forward packets from your LAN interface to your tunnel interface for packets destined for the internet ie the 2001::/3 global address prefix

Iv not figured out where to put this stuff so it persists after a reboot. Im using a virtual machine for this and I just suspend it at the moment.

Sorry my response is fairly vague, but this is as far as I've got at the moment.

---

### Post by superdupont on 2009-10-20
thanks but as I said, I don't know much about networking, so you mostly spoke chinese to me here :)
I just have one computer. at home.
 and the route2 example is of little use "as is", as it just throws me an error from the very first line :[SIZE=2]
[/SIZE]
modprobe ipv6
[SIZE=2]ip tunnel add he-ipv6 mode sit remote 216.66.xx.xx local 90.xx.xxx.xxx ttl 255
ip link set he-ipv6 up
ip addr add 2001:470.xxx.xx::2/64 dev he-ipv6
ip route add ::/0 dev he-ipv6
ip -f inet6 addr

[/SIZE]the modprobe ipv6 gives me 
"FATAL: Module ipv6 not found."

no idea what that means (Is it normal on Ubuntu ?). as far as I know, my Ubuntu can handle ipv6 as I was previously on a different ISP with native ipv6 support and it worked like a charm without having to ask anyone a tunnel. Good old times :popcorn:

just in case, I just ignored the modprobe line and typed the 2nd line "ip tunnel add" etc
that gives me a luvely...
**[*ioctl*: *No such device*]("http://www.linuxquestions.org/questions/linux-networking-3/ioctl-no-such-device-mist-18296/")**


so well, the route2 script "out of the box" doesn't seem that adequate to Ubuntu...

---

### Post by movieman on 2009-10-20
Ubuntu certainly handles ipv6 because I have an ipv6 network running at home. If you can't load the ipv6 module then presumably either the modprobe line is incorrect or you need to install something extra to get that module: it just worked for me, so I can't point you in the right direction.

---

### Post by superdupont on 2009-10-20
ok I know now ipv6 is compiled in the kernel since 9.04 at least, so that's not the obstacle here. let's forget that modprobe thing and concentrate on line 2, ie why :
[SIZE=2]
ip tunnel add he-ipv6 mode sit remote 216.66.xx.xx local 90.xx.xxx.xxx ttl 255
gives me "IOCTL : no such device ?"

do I need to add/edit some config file before running this ? should I see the "sit" thingie below eth0 when I run ifconfig BEFORE I type ip tunnel add or is this command that's supposed to create that sit device ?

coz for now I have nothing...

eth0      Link encap:Ethernet  HWaddr 00:23xx.65.x:7e  
          inet adr:192.168.x.xx  Bcast:192.168.x.xx  Masque:255.255.255.0
          adr inet6: fe80::223.xxx.xxx.xxx/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:5093227 erreurs:0 :0 overruns:0 frame:0
          TX packets:2809174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4944923444 (4.9 GB) Octets transmis:5347417393 (5.3 GB)
          Interruption:251 Adresse de base:0x6000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:724 erreurs:0 :0 overruns:0 frame:0
          TX packets:724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:88006 (88.0 KB) Octets transmis:88006 (88.0 KB)




[/SIZE]

---

### Post by Wordan on 2009-10-20
You should put sudo infront of those commands I think.  eg:

sudo ip tunnel add he-ipv6 mode sit remote 216.66.xx.xx local 90.xx.xxx.xxx ttl 255

---

### Post by superdupont on 2009-10-20
> **Wordan said:**
> You should put sudo infront of those commands I think.  eg:

sudo ip tunnel add he-ipv6 mode sit remote 216.66.xx.xx local 90.xx.xxx.xxx ttl 255

...
lol, ok you obviously caught me in a "can't shoot an elephant in a corridor" scenario. 
Can't believe I didn't even think of it  :p

ok, so (sudo +) 
ip tunnel add : worked
ip link set : worked (I have now my new "device" appearing with ifconfig)
the rest after dinner. stay tuned  :)

---

### Post by superdupont on 2009-10-20
so I took a shortcut, put the whole 
[SIZE=2]> 
ip tunnel add he-ipv6 mode sit remote 216.66.xx.xx local 90.xx.xxx.xxx ttl 255
ip link set he-ipv6 up
ip addr add 2001:470.xxx.xx::2/64 dev he-ipv6
ip route add ::/0 dev he-ipv6
ip -f inet6 addr


in a script, ran it (with sudo :P ), and ...well, I have my he-ipv6 device...but I still can't use IPV6 :mad:

ie ifconfig gives me now :
eth0      Link encap:Ethernet  HWaddr 00:23:54:65:98:7e  
          inet adr:192.168.x.xx  Bcast:192.168.x.xx  Masque:255.255.255.0
          adr inet6: fe80::223:54ff.xxxx.xxx/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4144 erreurs:0 :0 overruns:0 frame:0
          TX packets:4332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2056392 (2.0 MB) Octets transmis:547588 (547.5 KB)
          Interruption:251 Adresse de base:0x6000 

he-ipv6   Link encap:IPv6-dans-IPv4  
          adr inet6: 2001:470[/SIZE][SIZE=2].xxxx.xxx[/SIZE][SIZE=2]::2/64 Scope:Global
          adr inet6: fe80::[/SIZE][SIZE=2].xxxx.xxxx[/SIZE][SIZE=2]/128 Scope:Lien
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:48 erreurs:0 :0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:5746 (5.7 KB) Octets transmis:5746 (5.7 KB)

---------
[/SIZE][SIZE=2]
ip -f inet6 addr[/SIZE][SIZE=2]      returns :

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 fe80::[/SIZE][SIZE=2]xxxx.xxxx[/SIZE][SIZE=2]:fe65:987e/64 scope link 
       valid_lft forever preferred_lft forever
6: he-ipv6@NONE: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1480 
    inet6 2001:470[/SIZE][SIZE=2].xxxx.xxx[/SIZE][SIZE=2]::2/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::[/SIZE][SIZE=2]xxxx.xxxx[/SIZE][SIZE=2]/128 scope link 
       valid_lft forever preferred_lft forever
----------------

sounds like a good start but I need something else as zero ipv6 website sees me as ipv6...

I also tried in addition 
> 
sudo /etc/init.d/networking restart

just in case. doesn't change anything

AND I checked in firefox ipv6 was allowed
> network.dns.disableIPv6;false

AND I tried with chromium too.
still nothing.

AND I checked there wasn't some annoying active firewall in the isp box (put the local ip in DMZ to be sure...)
again nothing...

Clueless...


[/SIZE]

---

### Post by Wordan on 2009-10-20
When setting up the tunnel try the ip command without specifying the local address. I found that worked for me.

ip tunnel add he-ipv6 mode sit remote 216.66.xx.xx

Check you can ping googles ipv6 website
ping6 2001:4860:a005::68

If that does work and you can't access websites, perhaps you have a DNS problem.
dig AAAA ipv6.google.com


Thats the extent of my ipv6 experience so far. I'm still trying to figure out an ipv6 only network in Virtualbox.

---

### Post by superdupont on 2009-10-21
damn, you're right (...again), ipv6 works with ip adresses, it's a DNS resolution problem.
so I added an ipv6 dns server ip in /etc/resolv.conf, and it works...

(new) PROBLEM : if I restart network/reboot pc, the resolv.conf is rewritten (deleting ipv6 dns entry), even if I change permissions on the file...
Is there a way I can prevent this from happening so I don't have to edit /etc/resolv.conf each day ?

---

