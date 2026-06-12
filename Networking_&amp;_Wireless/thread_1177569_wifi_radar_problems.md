---
title: "wifi radar problems"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by kehon on 2009-06-03
wifi radar wont launch

```
su-to-root -X -c /usr/sbin/wifi-radar
Traceback (most recent call last):  File "/usr/sbin/wifi-radar", line 1616, in <module>
    auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'

```

thus after exceuting it a couple of times but first two times did nothing although it did it before like this also any fix for this cause wifi radar not working

---

### Post by RadarBat on 2009-06-20
> **kehon said:**
> wifi radar wont launch

I have the same problem.  "Could not launch wifi-radar. Failed to execute child process "su-to-root" (No such file or directory.)"

Tried to install su-to-root - no such package.

What now?    RB

---

### Post by radixor on 2009-06-21
> **kehon said:**
> wifi radar wont launch

```
su-to-root -X -c /usr/sbin/wifi-radar
Traceback (most recent call last):  File "/usr/sbin/wifi-radar", line 1616, in <module>
    auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'

```

thus after exceuting it a couple of times but first two times did nothing although it did it before like this also any fix for this cause wifi radar not working

Looks like wifi-radar is returning a list object instead of a comma seperated string, a fix would be to add
```

if isinstance(auto_profile_order, basestring):
   auto_profile_order = auto_profile_order.split(',')

```
as a replacement to line 1616. See, what that gives you? Make sure save a backup copy first:) This is of course, assuming you understand python..

---

### Post by RadarBat on 2009-06-21
I don't understand python. Where can I go to find an un-broken wifi-radar?  RB

Or can you tell me how to fix it?

---

### Post by kerry_s on 2009-06-21
you could try "network-config".
**sudp apt-get install network-config**

make the launcher, command> **gksudo network-config**

i use /etc/network/interfaces for my main connection and network-config if i want to jump on other networks.

---

