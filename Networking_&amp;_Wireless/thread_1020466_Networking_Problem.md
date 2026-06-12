---
title: "Networking Problem"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by gastly on 2008-12-24
Hi everyone,
I have this major problem with Kubuntu (and also Ubuntu, tried with both.)
I connect to the internet via a network (which is my ISP's network) and when I installed (K)Ubuntu on my computer, it does not connect to the internet.
Here is a summary of my network configuration:
[B]
In-built network card name: Realtek RTL8168
My Computer's Static Address: 10.1.126.38
ISP's gateway address: 10.1.126.1
Netmask: 255.255.255.0
DNS Address: 192.168.222.3,202.88.149.6[/B]

When I try to ping my ISP's gateway (which is 10.1.126.1) it gives this:

```

ping 10.1.126.1
PING 10.1.126.1 (10.1.126.1) 56(84) bytes of data.
From 10.1.126.38 icmp_seq=1 Destination Host Unreachable
From 10.1.126.38 icmp_seq=2 Destination Host Unreachable
From 10.1.126.38 icmp_seq=3 Destination Host Unreachable
^C
--- 10.1.126.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4007ms, pipe 3

```

And when I try to ping my own address, it works and gives this:
```

ping 10.1.126.38
PING 10.1.126.38 (10.1.126.38) 56(84) bytes of data.
64 bytes from 10.1.126.38: icmp_seq=1 ttl=64 time=0.033 ms
64 bytes from 10.1.126.38: icmp_seq=2 ttl=64 time=0.032 ms
64 bytes from 10.1.126.38: icmp_seq=3 ttl=64 time=0.034 ms
64 bytes from 10.1.126.38: icmp_seq=4 ttl=64 time=0.028 ms
^C
--- 10.1.126.38 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms

```

To try to solve this on my own, I first removed network-manager and **Knetwork-manager** (on a fresh install of kubuntu).
Then I edited the files, **/etc/network/interfaces** and **/etc/resolv.conf** and added all the things manually.
But still, nothing works, I'm all frustrated!
And also, the network never worked with earlier Ubuntu versions except Dapper.
I dual-boot my Kubuntu with XP Pro and XP has never had any problems with this.

Here are the contents of the files which I edited:
**/etc/network/interfaces**
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 10.1.126.38
netmask 255.255.255.0
gateway 10.1.126.1
auto eth0

```

**/etc/resolv.conf**
```

nameserver 192.168.222.3
nameserver 202.88.149.6

```

---

### Post by superprash2003 on 2008-12-24
post output of ifconfig.. doesnt your connection need a dialer or anything of that sort?? like a username and password??

---

### Post by gastly on 2008-12-24
Hi superprash2003 :)
Sorry, forgot to post the **ifconfig** output.
Here it is:
```

**ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:e0:24:c9
          inet addr:10.1.126.38  Bcast:10.1.126.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2760204557 overruns:0
frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000

```

And yes, my ISP does require a dialer to login, but it's only required for logging in and accessing the internet. But still, pings should work without even logging in with the dialer, it works with XP.

---

### Post by gastly on 2008-12-25
bump.
Can anyone please help me to solve this problem?

---

### Post by ilpiero on 2008-12-30
Same problem as gastly,(fresh install,static ip,Kubuntu 8.10).I can't manage to make my network work.
On my 8.04 works perfectly

---

### Post by nzadLithium on 2008-12-30
are you connecting through a router? Ie does your computer plug into a router/modem that then goes into the telephone line, through to your isp?

---

### Post by gastly on 2008-12-30
> **nzadLithium said:**
> are you connecting through a router? Ie does your computer plug into a router/modem that then goes into the telephone line, through to your isp?

Well, in my case, my ISP has given has connected my computer with a LAN cable, nothing else is given by my ISP. They just got a cable, plugged it into my computer, installed their dialer (on windows) configured the connection, took the money and flew, lol.
But seriously, the LAN cable goes into a black box installed outside our house (that could be something, dunno what, sorry for the n00b talk).
They just connect me through a gateway, it could be that they gave me a connection through their router which is installed on their place (seeing that it's a local ISP, they have their office just a couple of blocks away).

---

### Post by Bruce M. on 2008-12-30
> **gastly said:**
> Hi everyone,
I have this major problem with Kubuntu (and also Ubuntu, tried with both.)
I connect to the internet via a network (which is my ISP's network) and when I installed (K)Ubuntu on my computer, it does not connect to the internet.

The problems, as I've learned, is with "network-manager".

Check this out in the kbuntuforums: [Howto: Ethernet connection without a GUI]("http://kubuntuforums.net/forums/index.php?topic=3100052.0")

I did a modify of that for my Xubuntu setup.
Works for Ubuntu as well, just need to change a few commands:

for Xfce and Gnome: network-manager-gnome network-manager and use mousepad or gedit.

Hope this helps.
Bruce

---

### Post by gastly on 2008-12-30
> **Bruce M. said:**
> The problems, as I've learned, is with "network-manager".

Check this out in the kbuntuforums: [Howto: Ethernet connection without a GUI]("http://kubuntuforums.net/forums/index.php?topic=3100052.0")

I did a modify of that for my Xubuntu setup.
Works for Ubuntu as well, just need to change a few commands:

for Xfce and Gnome: network-manager-gnome network-manager and use mousepad or gedit.

Hope this helps.
Bruce
Hiya Bruce :)
Thanks for the info, but I've done **exactly** the same things that has been mentioned in the link you gave, still no luck. The configuration is 100% correct (as far as I know). I think this could be some router problem...
Just one question, can a router block packets from a specific OS? I think not (but I could be wrong), 'cause WinXP works 100% with this connection, could this be that they only allow sending packets by Windows platform? (Sounds, crazy, but my crazy mind usually thinks lots of crazy stuff like this :P )

---

### Post by Iowan on 2008-12-30
> **gastly said:**
> 
Just one question, can a router block packets from a specific OS? I think not (but I could be wrong), 'cause WinXP works 100% with this connection, could this be that they only allow sending packets by Windows platform? I'm probably off base, too, but I wonder if IPv6 may be causing problems?

---

### Post by gastly on 2008-12-30
hmmm...I didn't think of that, I'll try and disable IPv6 and then check, but I gotta reboot the whole `puter to do it and I'm doing some important stuff on it right now ;)
So, I'll try tomorrow and then post the results :)
Thanks ;)

---

### Post by Detonate on 2008-12-30
> **gastly said:**
> 
Just one question, can a router block packets from a specific OS? 

Depending on the router, it could be setup to block specific addresses from a specific machine using the MAC address.  But unless someone intentionally did a lot of work to cause that to happen, it certainly would not happen.

---

### Post by gastly on 2008-12-31
[quote=Iowan]i'm probably off base, too, but i wonder if ipv6 may be causing problems?[/quote]

I tried disabling ipv6, but still no luck. The same old problem...

[quote=Detonate]Depending on the router, it could be setup to block specific addresses from a specific machine using the MAC address. But unless someone intentionally did a lot of work to cause that to happen, it certainly would not happen.[/quote]

hmmm...I see, but the MAC address would remain same if I'm on the same machine, right? And yeah, as you said, it would take a lot of work for someone to block a MAC address,why would anyone do that...at least my ISP won't, lol.

---

### Post by oygle on 2008-12-31
One of those IP's in the dns side of things looks strange. Here is what a lookup says about it

> 192.168.222.3 is part of a special address block (192.168.0.0 - 192.168.255.255) that is reserved for private networks.
See RFC 1918 for more information.

Shouldn't the name servers be ..

> 202.88.130.67
202.88.130.15

Oygle

---

### Post by oygle on 2008-12-31
> **gastly said:**
> 
ISP's gateway address: 10.1.126.1


That IP is a 'blackhole ..

> 10.1.126.1 is part of a special address block (10.0.0.0 - 10.255.255.255) that is reserved for private networks.
See RFC 1918 for more information.

Ask your ISP to supply you with the correct IP address, and also the correct name servers.

---

### Post by gastly on 2008-12-31
hmmm...well actually, as the lookup says:
> 10.1.126.1 is part of a special address block (10.0.0.0 - 10.255.255.255) that is reserved for private networks.
These are for private networks and as I mentioned before, my ISP has set up a private network of all of their customers residing in a specific locality.

Here is how we get connected to the internet:
First is the gateway of our local ISP, then there is the main ISP's internal network (in my case Hathway) and **then** it goes through from the ISP's network to the outside world (internet).

I hope I made this clear, hehe. So, there is absolutely nothing wrong with the IP's, as I mentioned before, it works on Windows, so nothing is wrong with it.

Cheers :)

- gastly

PS: A very happy new year in advance to all of ya! :D

---

### Post by gastly on 2009-01-09
Hi all, just an update, I just tried Puppy Linux (from Live CD) and, although I needed to compile the drivers for my card, it worked like a charm!
So, I think, this is not a router issue, probably something in my (K)Ubuntu.
Any more ideas? :|

---

