---
title: "Problems with loopback (lo)"
date: 2006-04-06
forum: Networking &amp; Wireless
---

### Post by OliverW on 2006-04-06
A friend asked me to help him with his ubuntu machine and specifically with his network connection. I'm fairily familair with Debian so I had a look. 

The problem was initially that his eth0 didn't come up during boot time but could be brought up afterwards (with ifup for example). After some investigation it turns out that his loopback interface is down and cannot be brought up with ifup or /etc/init.d/networking restart, it comes back with: 

```
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces
```

I've been searching all over the place but the reference for lo in /network/interfaces is correct:

```

auto lo
iface lo inet loopback

```

I've searched all over de place for the */etc/network/interfaces:1: misplaced option* error but could not really find it (neither on google). 

BTW: as far as I know this is on Ubuntu 5.10 with kernel 2.6.12-9-386

Some help would be very appreciated :)

---

### Post by OliverW on 2006-04-06
Solved the problem. For some reason there was a weird (invisible for VIM) character in the first line. I spotted it by doing a 'cat' on the file:

```
ï»¿# Loopback
auto lo
iface lo inet loopback
```

---

### Post by TheRealMikeD on 2007-02-25
I had a similar problem with ifup not being able to read /etc/network/interfaces, reporting the "misplaced option" error message.  I eventually figured it out.  The comment at the top which was inserted by the installer had a line break in it, like so:

# This file describes the network interfaces available on your system 
and how to activate them. For more information, see interfaces(5).

Notice that on the second line, there is no "#" character, so ifup was trying to interpret this line.

The top section of the file should look like this:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

Hope this helps someone!
-Mike D.

---

