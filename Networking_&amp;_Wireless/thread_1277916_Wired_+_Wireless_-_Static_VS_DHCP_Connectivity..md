---
title: "Wired + Wireless - Static VS DHCP Connectivity."
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-09-28
I have an Ubuntu laptop that runs as a mobile FOG server which does Windows imaging.

I have a static IP set in the interfaces file for 192.168.1.100

I leave my wireless as dhcp.

I like that so I can get updates wirelessly and use the wired connectivity for imaging since it's a gigabit port. 

I just tried to connect to my Samba server at home to grab something and I couldn't hit it. Yet I have a valid IP address and my router's DHCP page confirms it. To get to my Samba server, I had to take out the static IP of my wired network card, then it managed to hit my server wirelessly.

Why is it that it takes priority like that? Logic would suggest that it'll go to whichever connection can grab the destination, which in this case would have been wireless since wired was static and disconnected.

Any input?

---

### Post by slakkie on 2009-09-29
Wired and wireless are in the same network segment?

Then change your metric on one of the interfaces.
Add it to your interfaces file and restart your networking.

eg

```

iface home-fixed2 inet static
    address 192.168.1.14
    netmask 255.255.255.0
    gateway 192.168.1.254
    metric 1

iface home-wifi2 inet static
    address 192.168.1.114
    netmask 255.255.255.0
    gateway 192.168.1.254
    metric 20

```

home-fixed2 has preference over home-wifi2 when connected via 2 interfaces.

---

### Post by shredder12 on 2009-09-29
I don't mean to hijack this thread... but I have similar problem

What's the use of defining metric for each interface..??

I am a bit confused here.. I didn't understand the logic behind the solution ..
could you plz explain it ??

---

### Post by slakkie on 2009-09-29
The problem is that without the metric you will have 2 interfaces used for the same destinations. It will use either interface, which causes problems with the routing table.

By setting a metric you can avoid this, since the higher metric is more "expensive" to use. So the OS will use the interfaces with the lowest metric if it needs to route traffic. In case the lower metric interface is shutdown it will use the higher metric interface since it is the only interface which can be used to route traffic towards that particular network/destination.

See also [http://en.wikipedia.org/wiki/Metrics_%28networking%29](http://en.wikipedia.org/wiki/Metrics_%28networking%29)

The problem could also be solved by adding static routes, but that is used mostly to make sure specific networks/hosts are routed via a different interface then the default. You then force only those hosts to use link B even though normally the OS would use link A.

---

### Post by Roasted on 2009-09-29
> **slakkie said:**
> Wired and wireless are in the same network segment?

Then change your metric on one of the interfaces.
Add it to your interfaces file and restart your networking.

eg

```

iface home-fixed2 inet static
    address 192.168.1.14
    netmask 255.255.255.0
    gateway 192.168.1.254
    metric 1

iface home-wifi2 inet static
    address 192.168.1.114
    netmask 255.255.255.0
    gateway 192.168.1.254
    metric 20

```

home-fixed2 has preference over home-wifi2 when connected via 2 interfaces.

The other thing is, my wired LAN doesn't have a gateway. You see, I image from my laptop and I use a local LAN setup using a 24 port switch. I don't need or want external access, so I just set up an IP with the subnet in the interfaces file and bam - I can image just fine. Would me not needing a gateway be an issue for this at all?

---

### Post by shredder12 on 2009-09-29
Actually I think the path completely depends upon the interface chosen.
if this is your wired interface then it will directly connect to the host IP..( or a switch/router if there is one)
and
if wireless interface is selected then the path would be through a router..

so, i mean to say a path is decided after the selection of interface (or network).. a network or interface is not decided on its basis..

I don't have the solution to this problem.. but a gateway doesn't seem to be an issue..

This is what I think,,.. I may be wrong..

---

### Post by slakkie on 2009-09-29
> **Roasted said:**
> The other thing is, my wired LAN doesn't have a gateway. You see, I image from my laptop and I use a local LAN setup using a 24 port switch. I don't need or want external access, so I just set up an IP with the subnet in the interfaces file and bam - I can image just fine. Would me not needing a gateway be an issue for this at all?

You can remove the gateway entry, it will not route anything via your fixed lan..

---

