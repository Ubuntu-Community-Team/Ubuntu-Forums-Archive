---
title: "subnet question"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Cr0n_J0b on 2011-01-22
I'm really confused on the whole subnet mask stuff.  I've read a bunch but it just confuses me more.  I know that I need something like 255.255.255.0 for a full class C network, but I'm bridging 2 networks together.  192.168.1.0/24 and 192.168.2.0/24.  I sort of assumed that if I put them both on the same switch and link them together I should be able to see the other computers...assuming that my subnet mask is something broader than 255.255.255.0.   So I tried 255.255.0.0 and 255.255.254.0..

Then I noticed that one of my systems has no issues with hitting computers on 192.168.2.0/24 even though it has a mask of 255.255.255.0 

Boy, I'm confused...really.

essentially what I'm trying to do is this.

Network A -- Internal LAN 192.168.1.0/24
Network B -- WAN interface to cable modem
Network C -- Internal LAN 192.168.2.0/24
Network D -- WAN interface

I have a couple of firewalls...

first network:

          Internet (B)       Internet (D)
              ^                  ^
              |                   |
A <--->router FW <-->router FW <---->C

The reason i'm doing this is because C is all my wifi stuff and because a lot of it's bridged, I'm just going to run a captive portal.  But, there are a few clients that I want to get in to network A.  I don't plan to use VPN or anything more fancy than mac filtering and pass through to get people from C to internet, but since C is on a different subnet what does the mask need to be at the various links?

thanks

---

### Post by Cr0n_J0b on 2011-01-22
bump up

---

### Post by redmk2 on 2011-01-22
> **Cr0n_J0b said:**
> I'm really confused on the whole subnet mask stuff.  I've read a bunch but it just confuses me more.  I know that I need something like 255.255.255.0 for a full class C network, but I'm bridging 2 networks together.  192.168.1.0/24 and 192.168.2.0/24.  I sort of assumed that if I put them both on the same switch and link them together I should be able to see the other computers...assuming that my subnet mask is something broader than 255.255.255.0.   So I tried 255.255.0.0 and 255.255.254.0..

Then I noticed that one of my systems has no issues with hitting computers on 192.168.2.0/24 even though it has a mask of 255.255.255.0 

Boy, I'm confused...really.

Subnet masks describe (define) the borders of individual subnets (the broadcast domain).  The routers will allow traffic between these domains (Layer 3).  What you can't do is Layer 2 (switched) only traffic.  Ethernet is Layer 2 and TCP/IP is Layer 3.  

As far as subnet masks, I find it better to see this in a binary form.  The first subnet of 192.168.1.0/24 (the /24 is the 24 bit mask) looks like this```
[COLOR="Red"]**110000001010100000000001**[/COLOR][COLOR="Blue"]**00000000**[/COLOR]
```
The red is 24 bits of mask (255.255.255) for the network and the blue is the 8 bits of host addressing (a total of 32 bits).  Note that each digit is represents a bit.  The decimal value may change but a bit is a bit.
Here is the subnet 192.168.2.0/24 in binary form```
[COLOR="Red"]**110000001010100000000010**[/COLOR][COLOR="Blue"]**00000000**[/COLOR]
```

Here they are together so you can see the difference```
[COLOR="Red"]**11000000101010000000000[B][COLOR="Green"]1[/COLOR]**[/B][/COLOR][COLOR="Blue"]**00000000**[/COLOR] = 192.168.1.0/24
[COLOR="Red"]**1100000010101000000000[B][COLOR="Green"][B]1**[/COLOR][/B]0[/B][/COLOR][COLOR="Blue"]**00000000**[/COLOR] = 192.168.2.0/24
```

The smallest single network you can have would be 192.168.0.0/22 (s/m 255.255.252.0).  This will provide you with this```

New start:	192.168.0.0	 = **[COLOR="Red"]1100000010101000000000[/COLOR]****[COLOR="Blue"]0000000000[/COLOR]**
New end:	192.168.3.255	 = **[COLOR="red"]1100000010101000000000[/COLOR]****[COLOR="blue"]1111111111[/COLOR]**

```
> 

essentially what I'm trying to do is this.

Network A -- Internal LAN 192.168.1.0/24
Network B -- WAN interface to cable modem
Network C -- Internal LAN 192.168.2.0/24
Network D -- WAN interface

I have a couple of firewalls...

first network:

          Internet (B)       Internet (D)
              ^                  ^
              |                   |
A <--->router FW <-->router FW <---->C

The reason i'm doing this is because C is all my wifi stuff and because a lot of it's bridged, I'm just going to run a captive portal.  But, there are a few clients that I want to get in to network A.  
In from where?  The internet or Net_C?> 
I don't plan to use VPN or anything more fancy than mac filtering and pass through to get people from C to internet, but since C is on a different subnet what does the mask need to be at the various links?

I'm not sure what you are trying to achieve in the end.  Maybe a drawing of the network topology will make it clearer.

If you are just searching for a singe subnet for the entire network (of the 2 subnets) then it will be as I said; 192.168.0.0/22.  The subnet mask for a /22 network is 255.255.252.0 .

---

