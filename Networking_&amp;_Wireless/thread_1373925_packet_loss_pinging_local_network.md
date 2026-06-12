---
title: "packet loss pinging local network"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by mistknight on 2010-01-06
Hello all,

I'm using kubuntu 9.10 desktop edition as a server and I set the IP statically, what happens is that when I ping it from another machine on the same network, I get intermittent packet loss (up to 80% and sometimes even higher). When I ping any other machine on the local network everything's fine with 0% packet loss. Packets go directly through switch, no router or anything in between.

I suspected wiring issues, but that doesn't seem to be the problem after I changed the wiring. I was connected to wireless and suspected that but no go either. Same thing when I turn wired. I just changed the ethernet card suspecting drivers but that's no good either.

Iptables is a cleanslate installation, it's totally empty.

I don't even know where to begin debugging such a problem. How do I go about debugging the issue? Any help appreciated!

---

### Post by sedawk on 2010-01-06
Do you have package loss in both directions, e.g pinging the
server A from box B and pinging box B from server A.

Have you turned off all the other network interfaces?
(Connecting one computer with different wired/wireless
 interfaces to the same subnet can have really nasty
 side effects!).

You can change ports on the switch or you can connect
a notebook or similar directly to the server (cross-link
cable and static IP on both machines) for further testing ...

---

### Post by mistknight on 2010-01-06
I just tested. The packet loss is both ways. Notice that the problem is pinging from ANY box to the server and from the server to ANY box, not from one box in particular.

I just changed the ethernet cable and same behavior, and as I stated earlier, I changed the ethernet card altogether but the problem still persists.

I'm highly inclined to say it's an issue on the server, but just don't know what it is or how to figure it out.

As to the multi interfaces, not totally sure how I can check for that. For starters, I'm pasting my /etc/network/interfaces file


```
auto lo
iface lo inet loopback
auto eth2
iface eth2 inet static
address 192.168.0.39
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

This is the result of ifconfig

```
eth2      Link encap:Ethernet  HWaddr 00:08:a1:4e:04:c8
          inet addr:192.168.0.39  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe4e:4c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38338 errors:894 dropped:0 overruns:0 frame:0
          TX packets:30035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9997892 (9.9 MB)  TX bytes:21182186 (21.1 MB)
          Interrupt:20 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1224262 (1.2 MB)  TX bytes:1224262 (1.2 MB)
```

Furthermore, this is a tracepath from my box (192.168.0.174) to the server (192.168.0.39)

```
 1:  fin-aymand.jeeranoffice.local (192.168.0.174)          0.253ms pmtu 1500
 1:  jdev.jeeran.local (192.168.0.39)                      11.607ms reached
 1:  jdev.jeeran.local (192.168.0.39)                       1.929ms reached
     Resume: pmtu 1500 hops 1 back 64
```

I do see something peculiar though. My machine's hostname is "mk", not "fin-aymand.jeeranoffice.local" if that makes any difference.

Appreciate any help in solving this!

---

### Post by Iowan on 2010-01-06
I've seen other threads where the problem was solved by tweaking the MTU (via **ifconfig**). 1492 seems to be a familiar number.

---

### Post by chili555 on 2010-01-07
Your *interfaces* file looks a bit busy. I suggest amending it to:```
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet static
address 192.168.0.39
netmask 255.255.255.0
gateway 192.168.0.1
```Are you pinging by name or number? If by name, how are local names resolved to numbers?

May we please see:```
sudo ethtool eth2
```Thanks.

---

### Post by SecretCode on 2010-01-07
You do have receive errors on eth2. For an ethernet interface, there shouldn't be any (or at most one per restart). 

I suggest a reboot or an */etc/init.d/networking restart*, and look at ifconfig again.

I see you've changed the card and the cable. Have you changed the switch/hub the cable is plugged into? I think it's quite likely something is causing link errors.


> **Iowan said:**
> I've seen other threads where the problem was solved by tweaking the MTU (via **ifconfig**). 1492 seems to be a familiar number.

MTU settings can affect connectivity - especially on wireless - but shouldn't make any difference to pings with the default 56 byte payload. I'd have thought.

---

### Post by Iowan on 2010-01-07
> **SecretCode said:**
> MTU settings can affect connectivity - especially on wireless - but shouldn't make any difference to pings with the default 56 byte payload. I'd have thought.True - most of the "problems solved" were for downloading web pages - not for pings.

---

### Post by mistknight on 2010-01-10
The problem is fixed. I WOULD LOVE it if someone explained why it occurred in the first place.

The problem was with the broadcast IP. When I commented it out the problem disappeared. But I don't understand why. Can a guru look deeply in my settings and let me know if they think I have it set wrong?

Also, could someone clarify how a mis-configured broadcast IP cause this huge problem?

Thanks!

---

### Post by pbrane on 2010-01-10
First the MTU of 1492 is ususally set to account for the 8 byte overhead of PPPoE. 1500 is max for Ethernet, although larger for gigabit Ethernet. (JumboFrames) 

Your config files look pretty much like mine, except that I do have the bcast address set and I don't have any errors or packet loss.

To get a better idea of the network config you could look at *man interfaces*, if you haven't already. Note the **KNOWN BUGS/LIMITATIONS** section about the kernel iface naming. Also look at the example section.

Maybe you could try putting that bcast address back in and restart your network to see if that really is the problem. And you are sure that xxx.xxx.xxx.39 is not in the DHCP pool?

---

### Post by maximaximax on 2010-05-25
Thank you, mistknight! It also solved my problem with Ubunti 10.04. I removed the broadcast line and now all works fine :)

---

### Post by maximaximax on 2010-05-25
Thank you, mistknight! Your solution also solved my problem with Ubuntu 10.04. I just removed the broadcast line in etc/network/interfaces and now all works fine :)

---

