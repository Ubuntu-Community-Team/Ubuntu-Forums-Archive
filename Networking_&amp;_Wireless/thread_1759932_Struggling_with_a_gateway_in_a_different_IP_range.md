---
title: "Struggling with a gateway in a different IP range"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by shakyj on 2011-05-16
Hey,

I am using Ubuntu Server 10.10 but I don't think it's an issue with the version.

My ISP have provided me with my IP and gateway.
IP = 188.94.x.x
Gateway = 92.42.10.25

No matter what I do I get "From 127.0.0.1 : ICMP_seq = 1 Destination Host Unreachable"

I have tried [http://ubuntuforums.org/showthread.php?t=1510986](http://ubuntuforums.org/showthread.php?t=1510986) to no avail.

route -n =
```
Destination   Gateway     Genmask      Flags Metric Ref Use IFACE
92.42.10.25   0.0.0.0   255.255.255.255 UH      0    0   0   eth0
0.0.0.0     92.42.10.25   0.0.0.0       UG      0    0   0   eth0
```

/etc/network/interfaces looks like
```

iface eth0 inet static
address 188.94.x.x
netmask 255.255.255.255
gateway 92.42.10.25
```

---

### Post by Iowan on 2011-05-16
You have verified this information with your ISP? Has this configuration worked on another machine?  I'm no expert, but something seems wrong with the IP, subnet, and gateway. :confused:
(I'm still trying to work through the link you provided...)

**ifconfig -a** confirms eth0 has proper address?

---

### Post by bab1 on 2011-05-16
> **shakyj said:**
> Hey,

I am using Ubuntu Server 10.10 but I don't think it's an issue with the version.

My ISP have provided me with my IP and gateway.
IP = 188.94.x.x
Gateway = 92.42.10.25

No matter what I do I get "From 127.0.0.1 : ICMP_seq = 1 Destination Host Unreachable"

I have tried [http://ubuntuforums.org/showthread.php?t=1510986](http://ubuntuforums.org/showthread.php?t=1510986) to no avail.

route -n =
```
Destination   Gateway     Genmask      Flags Metric Ref Use IFACE
92.42.10.25   0.0.0.0   255.255.255.255 UH      0    0   0   eth0
0.0.0.0     92.42.10.25   0.0.0.0       UG      0    0   0   eth0
```

/etc/network/interfaces looks like
```

iface eth0 inet static
address 188.94.x.x
netmask 255.255.255.255
gateway 92.42.10.25
```

Ahem...I'm still here from those good old days.  :-)

The first thing that I see off the top of my head is the /etc/networking/interfaces file looks unusual.  What (or why) the items in red```

iface eth0 inet static
address 188.94.x.x **[COLOR="Red"]<-- French ISP[/COLOR]**
netmask [COLOR="Red"]**255.255.255.255**[/COLOR]
gateway 92.42.10.25  **[COLOR="Red"]<-- Russian ISP[/COLOR]**

```

What command are you using to generate this response: "From 127.0.0.1 : ICMP_seq = 1 Destination Host Unreachable" ?

---

### Post by bab1 on 2011-05-16
> **Iowan said:**
> You have verified this information with your ISP? Has this configuration worked on another machine?  I'm no expert, but something seems wrong with the IP, subnet, and gateway. :confused:
(I'm still trying to work through the link you provided...)

**ifconfig -a** confirms eth0 has proper address?

In the link the OP provided, the question and the answer are provided in the first post (#1).

---

### Post by shakyj on 2011-05-17
> **bab1 said:**
> Ahem...I'm still here from those good old days.  :-)

The first thing that I see off the top of my head is the /etc/networking/interfaces file looks unusual.  What (or why) the items in red```

iface eth0 inet static
address 188.94.x.x **[COLOR="Red"]<-- French ISP[/COLOR]**
netmask [COLOR="Red"]**255.255.255.255**[/COLOR]
gateway 92.42.10.25  **[COLOR="Red"]<-- Russian ISP[/COLOR]**

```

What command are you using to generate this response: "From 127.0.0.1 : ICMP_seq = 1 Destination Host Unreachable" ?

The address and gateway were provided by the ISP. It's an English ISP so unsure why the gateway resolves to Russia. The actual IP on a geolocate resolves to a few miles from here. 

I have a few IPs from them and the windows box I am on now works fine with the IP below the one I am trying to get ubuntu server on.

The response was from a ping on my windows box on the IP below.

The only think I was unsure of on their instructions was the "VLAN IP Gateway 92.42.10.25/30" Unsure what the /30 is after.

-------------------------------------------------------------------------------------------------------------------------------------------------------------

Edit: Figured the gateway geolocate. The gateway is 92.42.120.25 not 92.42.10.25. I had done it right on the box just not when I typed it into here.

---

### Post by lz1dsb on 2011-05-17
That's impossible! Your IP address is from a different IP subnet from the Default Gateway. 
The role of the Default Gatway is to provide a way out of an IP subnet. That's why they need to be in the same network. And this isn't OS specific. It's networking.
/30 basically means that 30 bits from the 32 bit IPv4 address are assigned as an IP subnet number. This creates the following subnet mask 255.255.255.252.

---

### Post by bab1 on 2011-05-17
> **lz1dsb said:**
> That's impossible! Your IP address is from a different IP subnet from the Default Gateway. 
The role of the Default Gatway is to provide a way out of an IP subnet. That's why they need to be in the same network. And this isn't OS specific. It's networking.

Hold on here a minute.  The default GW is the route to take when no other route is known.  It is perfectly legitimate to to have a route to a host (router with public IP) that provides internet access and that route can be the default gateway.  Not only is it theoretically correct it has been done on may occasions.  The network manager has to know that the host he is using for a GW really is a gateway though.  You can add a route and make it the GW.  Follow the link in the first post of this thread.

See the man pages for route. 
> 
/30 basically means that 30 bits from the 32 bit IPv4 address are assigned as an IP subnet number. This creates the following subnet mask 255.255.255.252.

And that makes the IP address part of a 4 number range.  Not including the NetID and the B'cast there is only room for 2 hosts on this net.  I myself have used this type of range for connecting routers together (i.e. a transit net)

[quote= shakyj]

The response was from a ping on my windows box on the IP below.[/quote]
Did you ping from the Ubuntu host?  What was the exact command (post it) and what was the exact response (post that too).

Post the contents of the /etc/hosts file and the /etc/network/interfaces files for the Ubuntu host.

---

### Post by lz1dsb on 2011-05-18
So let's wrap it up. Probably I wasn't too much clear in my first post.
/32 mask which is used in this case is wrong. It's called host mask. Which means that this mask allows only one valid address. It something that is used more or less in the networking world but only on special cases (like loopback interfaces for example) and not on normal hosts.
Second. There's a difference between default gateway and default route!
In a standart situation with normal hosts you don't need routing, so that's why the hosts use Default Gateway. And the Default Gateway should be from the same IP subnet. That's how the logic works.
Default routes are used on networking equipment where they basically control the logic in the routring table i.e. if there isn't a specific route to a particular destination, the default route is used.
 
Cheers,
Boyan

---

### Post by lisati on 2011-05-18
Hang on a moment: I did a check of the first IP address. It's UK based, not French.

---

### Post by shakyj on 2011-05-19
I decided it was easier if I contacted my ISP and got them to put the gateway in the same range :).

Thanks for all the help anyway :)

---

