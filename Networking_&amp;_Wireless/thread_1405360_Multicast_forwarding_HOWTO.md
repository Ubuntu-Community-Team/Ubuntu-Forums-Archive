---
title: "Multicast forwarding HOWTO?"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by Selmi on 2010-02-12
hi. I have computer connected to network which uses multicast to show television (iptv). It works great. What I want to achieve is to allow computers on my local network to get access for it, for this I need to enable multicast forwarding

system is Ubuntu 9.10 64bit, its connected to internet providers network using eth1 and to local netwok using eth0. NetworkManager takes care about everything, I didn't wrote anything to configure files myself.... Unfortunately computers from local network don't get any multicasts from outside network and NetworkManager doesn't seem to have any configuration opeions about it(or if it does I didn't found them)

There is surprisingly lot of unanswered questions about it, I found only one solution here, but it doesn't work for me.... [http://www.unixresources.net/linux/lf/58/archive/00/00/06/55/65582.html](http://www.unixresources.net/linux/lf/58/archive/00/00/06/55/65582.html)

any idea how to make it work? I used instructions found in thread I posted link above:

```
- Ensure the kernel has the following enabled by looking in the .config
    CONFIG_IP_MULTICAST
    CONFIG_IP_PIMSM_V2
    CONFIG_IP_MROUTE
    the NETLINK-related options

```    
  all these are enabled, NETLINK settings are available as modules

```
- echo 1 ]/proc/sys/net/ipv4/ip_forwarding to turn on IP forwarding

```
  for me its called ip_forward, i have it on and it seems its working, computer on local network don't have problems to access internet

```
- assuming devices are eth0 and eth1, add multicast to the routing table
    route add -net 224.0.0.0/4 dev eth0
    route add -net 224.0.0.0/4 dev eth1

```
  done

```
- start the pimd daemon

```
  and here I fail, i get error message:
```
pimd: 21:05:38.654 cannot enable multicast routing in kernel: Address already in use

```

here I am stuck...I tried smcroute but the result was the same. is there anything else I may try? To be honest I really don't know much about networking so I will need some howto for dummies if possible....

---

### Post by tgalati4 on 2010-02-12
I'm confused.  If one computer can see the multicast stream, what prevents the other computers from seeing it?  Are these computers on the same LAN?  How do you have the primary computer connected?

What messages do you get from the other computers if you use VLC (media-->open network-->rtp://224.0.0.0:1234)?  VLC has a messages/error console.  What errors are you seeing?

---

### Post by mips on 2010-02-12
[https://launchpad.net/bugs/362274](https://launchpad.net/bugs/362274)

---

### Post by e24ohm on 2010-02-12
> **Selmi said:**
> hi. I have computer connected to network which uses multicast to show television (iptv). It works great. What I want to achieve is to allow computers on my local network to get access for it, for this I need to enable multicast forwarding

system is Ubuntu 9.10 64bit, its connected to internet providers network using eth1 and to local netwok using eth0. NetworkManager takes care about everything, I didn't wrote anything to configure files myself.... Unfortunately computers from local network don't get any multicasts from outside network and NetworkManager doesn't seem to have any configuration opeions about it(or if it does I didn't found them)

There is surprisingly lot of unanswered questions about it, I found only one solution here, but it doesn't work for me.... [http://www.unixresources.net/linux/lf/58/archive/00/00/06/55/65582.html](http://www.unixresources.net/linux/lf/58/archive/00/00/06/55/65582.html)

any idea how to make it work? I used instructions found in thread I posted link above:

```
- Ensure the kernel has the following enabled by looking in the .config
    CONFIG_IP_MULTICAST
    CONFIG_IP_PIMSM_V2
    CONFIG_IP_MROUTE
    the NETLINK-related options

```    
  all these are enabled, NETLINK settings are available as modules

```
- echo 1 ]/proc/sys/net/ipv4/ip_forwarding to turn on IP forwarding

```
  for me its called ip_forward, i have it on and it seems its working, computer on local network don't have problems to access internet

```
- assuming devices are eth0 and eth1, add multicast to the routing table
    route add -net 224.0.0.0/4 dev eth0
    route add -net 224.0.0.0/4 dev eth1

```
  done

```
- start the pimd daemon

```
  and here I fail, i get error message:
```
pimd: 21:05:38.654 cannot enable multicast routing in kernel: Address already in use

```

here I am stuck...I tried smcroute but the result was the same. is there anything else I may try? To be honest I really don't know much about networking so I will need some howto for dummies if possible....

Are you trying to forward you multicasts over a link that doesn't allow multicasts?

---

### Post by mips on 2010-02-12
I always wondered why people quote entire posts, especially when they are long?

He is trying to forward it between two networks (separate ethernet adapters)on his PC, one connects to the ISP and the other connects to his local LAN.

Multicast stream from ISP---->(Eth0)-PC-(Eth1)---->Local LAN (PC's on this network need to receive the multicast stream from the ISP)

---

### Post by Selmi on 2010-02-12
> **tgalati4 said:**
> I'm confused.  If one computer can see the multicast stream, what prevents the other computers from seeing it?  Are these computers on the same LAN?  How do you have the primary computer connected?

What messages do you get from the other computers if you use VLC (media-->open network-->rtp://224.0.0.0:1234)?  VLC has a messages/error console.  What errors are you seeing?

internet provider's network which also streams tv is connected to my computer using eth1. on my computer everything works. another computer is connected to mine using eth0. on this computer normal internet works, but vlc (or ping 224.0.0.1) doesn't.
i will post here result from vlc player tomorrow, now i am not alowed to experiment with it, but considering that ping 224.0.0.1 will return with 1005 packet loss i expect vlc will have same problem

> **e24ohm said:**
> Are you trying to forward you multicasts over a link that doesn't allow multicasts?

I hope I don't, I mean local network is ordinary ethernet so I don't see any reason why it shouldnt work

---

### Post by tgalati4 on 2010-02-12
Now I understand what you are trying to do.  Perhaps you can relay your incoming rtp stream to a different outgoing address, say 239.255.100.100.  There may be issues simply repeating the 224 stream.

[http://en.wikipedia.org/wiki/IP_Multicast](http://en.wikipedia.org/wiki/IP_Multicast)

and

[http://en.wikipedia.org/wiki/Protocol_Independent_Multicast](http://en.wikipedia.org/wiki/Protocol_Independent_Multicast)

Perhaps reading up on pimd:

man pimd

---

### Post by Selmi on 2010-02-16
i was recommended completely different solution, igmp proxy from [http://sourceforge.net/projects/igmpproxy/](http://sourceforge.net/projects/igmpproxy/) . it works

---

### Post by troglobit on 2010-11-20
I'd just like to add my few cents.  An IGMP proxy is probably useful in smaller networks, but you can also use either [mrouted]("http://freshmeat.net/projects/mrouted") or [pimd]("http://freshmeat.net/projects/pimd"), the latter is available in Ubuntu and the former is easily made into a .deb by downloading the latest release.

The error you get above is likely due to your having installed both smcroute and pimd at the same time, that doesn't work.  The smcroute package usually starts its daemon immediately after installation and then steals the multicast routing capability (MRT_INIT).  So try removing smcroute and restart pimd, that will likely work.

If that doesn't work then remove the mulitcast routes you added above, you don't need them with dynamic multicast routing protocols such as pimd or mrouted.

I know you're already a happy camper, but hopefully this reply can help someone else. :-)

---

### Post by jdramer on 2012-06-13
Just to confirm what troglobit said, I was able to get this setup working using pimd. I used the same setup as above, but didn't install smcroute and didn't need to add the default multicast routes.

One thing to keep in mind, for the multicasting to route properly make sure that the TTL on the packets is greater than 1. There's some details on using iptables to address this at the following link.

[http://bda.ath.cx/blog/2009/01/24/multicast-routing-upnp-traffic-with-linux/](http://bda.ath.cx/blog/2009/01/24/multicast-routing-upnp-traffic-with-linux/)

---

### Post by CharlesA on 2012-06-13
Back to sleep you go..

---

