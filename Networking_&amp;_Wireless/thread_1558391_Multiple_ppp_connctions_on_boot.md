---
title: "Multiple ppp connctions on boot"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by bedlamp on 2010-08-22
Hi

I'm trying to set up my server (ubuntu 10.04 server) to dial multiple ppp connections on boot as well as setting up the interface they are bound to to have its own LAN ip (for ICS)

The page [here]("https://help.ubuntu.com/community/ADSLPPPoE") has some examples, some of which are almost what I want, but none quite get there. the closest is this one:
```
auto eth0
iface eth0 inet ppp
         pre-up /sbin/ifconfig eth0 up
         provider dsl-provider
         post-down /sbin/ifconfig eth0 down
```So my questions are: 
Where in there do you put the normal eth0 config (address, netmask, etc.)? (before the pre-up block? in the pre-up block? after it?)
Can you have multiple provider statements, and does this influence the second line at all?

---

### Post by relay_man on 2010-08-22
Hello and welcome

I think the man page for interfaces may be of some help to you.

At the terminal, type "man interfaces" (without the quotes)

---

### Post by bedlamp on 2010-08-22
Hi

I looked at the man page and it was helpful to a point. What it doesn't tell me is how to set it up so that it will dial bound to eth0 as well as configuring it an ip address. (you can't pass it static as well as ppp)

The only way that I can see to do it is to do it something like this:
```

auto eth0 inet static
        address x.x.x.x
        netmask x.x.x.x
        broadcast x.x.x.x
        post-up /usr/bin/pon connection1
        post-up /usr/bin/pon connection2
        pre-down /usr/bin/poff connection2
        pre-down /usr/bin/poff connection1

```

is there a better way of doing this?

---

