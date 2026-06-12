---
title: "How to restrict an application from internet acess?"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by qqqwwweee on 2009-07-29
Hi. I am not very familiar with iptables. All the manuals I have read tells me how to restrict internet comunication to certain ports or ipadresses (or sometimes users). What I need is different and in fact implemented in every basic windows firewall and I wonder if its so complex in linux or ubuntu.

I need to restrict internet acess on application level. Say not allow adobe reader to acces update server or whole internet. Or to block say /tmp/myprogram completely from internet acess.

And what to do when I want disallow all aplications to acess internet and only manually specify that i want say firefox only acess http port?
Is there simple way to do so?

---

### Post by Brandon Williams on 2009-07-31
I can't think of a way to restrict by program. However, you could make use of iptables support for restricting by group id to do something like this.

Consider your example of outgoing http access. You could create a new group called "internet", change the group of the firefox binary to "internet", turn on the set-gid bit for the firefox binary, and then create an iptables rule that only allows outgoing http traffic if the either the user is root or the group is internet.

```
$ sudo addgroup internet
$ sudo chown root:internet /usr/lib/firefox-3.0.12/firefox
$ sudo chmod s+g /usr/lib/firefox-3.0.12/firefox
$ sudo iptables -I OUTPUT -m owner ! --gid-owner internet --protocol tcp --dport 80 -j DROP
$ sudo iptables -I OUTPUT -m owner --uid-owner root -j ACCEPT
```

A method like this might be a bit of a pain to maintain, but I think it should work.

Hopefully someone can think of something that's easier to setup and maintain.

---

