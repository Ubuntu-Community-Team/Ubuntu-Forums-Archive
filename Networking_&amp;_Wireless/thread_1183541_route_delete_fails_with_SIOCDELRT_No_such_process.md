---
title: "route delete fails with SIOCDELRT: No such process"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by zongpog on 2009-06-10
Hi, 
  I have read the man page several times for route, and cannot work out how to delete a route to a host.

Offending entry is 167.6.6.6:
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
167.6.6.6       -               255.255.255.255 !H        - -          - -

```
The interface is eth0.  

I have tried all of these commands and include the responce [note that I cannot think of a reason to specify the interface eth0 but did just in case it would work].

# route del  167.6.6.6
SIOCDELRT: No such process

# route del  -host 167.6.6.6
SIOCDELRT: No such process

# /sbin/route del -host 167.6.6.6 dev eth0
SIOCDELRT: No such process

# /sbin/route del -host 167.6.6.6 
SIOCDELRT: No such process

# /sbin/route del -host 167.6.6.6 netmask 255.255.255.255
route: netmask 00000000 doesn't make sense with host route


Does anyone else know what this ought to be?

Regards, Z

---

### Post by regala on 2009-06-10
> **zongpog said:**
> Hi, 
  I have read the man page several times for route, and cannot work out how to delete a route to a host.

Offending entry is 167.6.6.6:
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
167.6.6.6       -               255.255.255.255 !H        - -          - -

```
The interface is eth0.  

I have tried all of these commands and include the responce [note that I cannot think of a reason to specify the interface eth0 but did just in case it would work].

# route del  167.6.6.6
SIOCDELRT: No such process

# route del  -host 167.6.6.6
SIOCDELRT: No such process

# /sbin/route del -host 167.6.6.6 dev eth0
SIOCDELRT: No such process

# /sbin/route del -host 167.6.6.6 
SIOCDELRT: No such process

# /sbin/route del -host 167.6.6.6 netmask 255.255.255.255
route: netmask 00000000 doesn't make sense with host route


Does anyone else know what this ought to be?

Regards, Z

yep, there's even an hint in the last command output :)
# /sbin/route del 167.6.6.6 netmask 255.255.255.255

---

### Post by zongpog on 2009-06-10
> **regala said:**
> yep, there's even an hint in the last command output :)
# /sbin/route del 167.6.6.6 netmask 255.255.255.255

your command did not work:

#  /sbin/route del 167.6.6.6 netmask 255.255.255.255
route: netmask 00000000 doesn't make sense with host route, 

Please note that this is a route to a host and _not_ a network.

... and if I try it without the netmask command as it hints at then it still won't work;  This is a command that I tried earlier and was noted in the original post.
# /sbin/route del 167.6.6.6 
SIOCDELRT: No such process

niether does : 
# /sbin/route del -host 167.6.6.6
SIOCDELRT: No such process

Does anyone else have any other ideas?

---

### Post by Iowan on 2009-06-10
Since the **route** results showed it as a **reject** route (!H) to a host, 
would **route del -host 167.6.6.6 reject** work?

---

### Post by zongpog on 2009-06-11
> **Iowan said:**
> Since the **route** results showed it as a **reject** route (!H) to a host, 
would **route del -host 167.6.6.6 reject** work?

Yep - This worked.  Thank-you.

I wondered whether this was one of the reasons the route del cmd failed - because of the Reject route.

---

