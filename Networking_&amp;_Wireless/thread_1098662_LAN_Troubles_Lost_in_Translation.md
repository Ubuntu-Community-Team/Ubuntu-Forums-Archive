---
title: "LAN Troubles: Lost in Translation"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by WolfyAU82 on 2009-03-17
I'm having trouble with the family LAN and I am trying to setup a connection between both my PC running Ubuntu 8.10 (64 Bit) and my father's Pc running Windows XP.  Both have their own firewalls, I'm using Firestarter and the other is using Outpost and the only connectivity has been with my PC accessing shared locations from the Windows PC.

I'm trying to get a fully operating LAN going, how do I go about this?

---

### Post by nixscripter on 2009-03-17
Are they directly connected, or is there a router in the middle? If not, then one of them will have to use IP masquerading to allow full connectivity (probably Linux, Windows is stupid).

---

### Post by WolfyAU82 on 2009-03-18
via Modem Router

---

### Post by nixscripter on 2009-03-18
So, if your network looks like this:

```

+---------------+
|               |
|   Win XP PC   |
|               |
+---------------+
       ^
       |
       |
       V
+---------------+                     OoooooooooooO
|               |                     o           o
|     Router    |-------------------> o Internet  o
|               |                     o           o
+---------------+                     OoooooooooooO
       ^
       |
       |
       V
+---------------+
|               |
|   Linux  PC   |
|               |
+---------------+


```

It shouldn't be too hard.

1. Router gets DHCP address from your ISP (through the modem).
2. Router uses NAT to hand out private IP addresses to other two boxes.
3. Each box runs DHCP to get the address from the router.

On Windows, Control Panel -> Network Connections and Settings -> Select "Use DHCP"

On Linux, if you use GNOME, the network manager applet should try to get a DHCP address when you plug thethernet cable in.

How to configure the router depends upon the exact model you have. That's what the manual is for.

Hope this helps.

---

