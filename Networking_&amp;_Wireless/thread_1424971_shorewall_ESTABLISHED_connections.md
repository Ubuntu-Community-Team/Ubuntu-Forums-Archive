---
title: "shorewall ESTABLISHED connections"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2010-03-08
Hello,

I use ubuntu 8.04 LTS at various sites as the main router/firewall, and it works very well - has done for years, since ubuntu 6.x - I use shorewall/squid/dansguardian.

Sometimes, I need to block unwanted outbound traffic, and so I edit /etc/shorewall/rules - but when reloading shorewall, those new rules only apply to new connections, not established connections.

I've tried putting a DROP line in the ESTABLISHED section, but it fails.

I'm also uncertain whether shorewall does, or indeed can, control established connections directly or not.

Whatever, I need to find a way to either drop all connections on a shorewall reload (a messy way... not my preference) or find out how to apply new rules to established connections.

Right now, I'd have to reboot my ubuntu box to kill all connections; Somewhat of an overkill!!!!

Thanks in advance for any assistance

SS

---

### Post by r939ick on 2010-03-09
> **sparky-steve said:**
> 
I'm also uncertain whether shorewall does, or indeed can, control established connections directly or not.


shorewall deliberately ensures that existing connections will not be dropped by changing firewall rules - that ensures that you can restart shorewall over ssh without risking it dropping your connection.

> 
Whatever, I need to find a way to either drop all connections on a shorewall reload
Does `conntrack -F` look close to what you want?

> 
or find out how to apply new rules to established connections.
I'm not sure how you mean this.  Most of the accept/drop decisions are made based on data in the SYN packet, which means they can only apply to new connections.  Allowing TCP conversations to continue once they've been allowed by the firewall rules is generally a good thing.  Can you give examples of the changes you're trying to make and what you expect the firewall to do?

---

### Post by sparky-steve on 2010-03-09
> **r939ick said:**
> shorewall deliberately ensures that existing connections will not be dropped by changing firewall rules - that ensures that you can restart shorewall over ssh without risking it dropping your connection.

I can certainly appreciate this; My reasons for wanting to change/close established connections are shown below.

>  Does `conntrack -F` look close to what you want?Interesting.... I'll have to try this later; It *seems* like it might work, especially (if I read it correctly) if I can specify a source IP using the -s filter.

> I'm not sure how you mean this.  Most of the accept/drop decisions are made based on data in the SYN packet, which means they can only apply to new connections.  Allowing TCP conversations to continue once they've been allowed by the firewall rules is generally a good thing.I agree that in general it's a good thing....

>   Can you give examples of the changes you're trying to make and what you expect the firewall to do?Yes... Absolutely....

In the home environment, I want to kick my kids off of the internet at a given time; I can do this with rules (automated, even) but it will not apply to established connections; They've recently discovered that if that start a game/msn video chat/whatever a few minutes before cutoff, they're just fine.

Similarly in corporate situations, I have various reasons for resetting / dumping any established connections on an IP-by-IP basis.

What I would prefer not to do, as per my original post, is to reset ALL connections - including that of my own IP and/or router IP address.  This is most certainly something I want to do on an IP-by-IP basis. I am hoping that with conntrack and the -s filter, I may be able to achieve that.

But for now, I'm in production environment, so will wait until I can test on the lab machines.

Cheers

SS

---

### Post by sparky-steve on 2010-03-09
Well, that didn't work out well at all.... :(

```
root@server:/etc/shorewall# conntrack -F -s 192.168.1.119
conntrack v0.9.12 (conntrack-tools): Illegal option `--src' with this command
Try `conntrack -h' or 'conntrack --help' for more information.
```

I'll keep trying, but if anyone has any ideas to add, please feel free....

To reiterate, I'm looking for a way of flushing / killing any established connections to/from a specific (internal) IP address.

SS

---

### Post by sparky-steve on 2010-03-09
OK. all sorted!

For those in the future that may want to know.....

man conntrack is very helpful

So, to disconnect someone (new & established) I have to:

1, create (a) rule(s) in /etc/shorewall/rules to drop/block the connections
2, in conntrack issue the following command:

```
conntrack -D -s 192.168.1.102
```

That will flush out all existing connections with src of 192.168.1.102. I did note that it can take up to a minute for it to work - skype seemed to take the longest (I could still send msgs from the src address for about 50 seconds).

To list all connections from 192.168.1.102 the code is:

```
conntrack -L -s 192.168.1.102
```

Thanks for pointing me in the right direction, r939ick.

SS

---

### Post by gmcc on 2010-06-09
"For those in the future that may want to know"

Dear Sir/Madam, 

Greetings From the Future. It is good here.

Although things have not changed much in lo, these three months. We still have the scourage of how to kill ESTABLISHED connections when using the shorewall firewall system.

Tis well to know those in the past were comforted by conntrack -D and conntrack -L.


thanks!!!
--
mike

---

### Post by bvidinli on 2013-01-04
This seems better, without using conntrack;

You can set BLACKLISTNEWONLY=No in shorewall.conf

---

### Post by howefield on 2013-01-04
Old thread closed.

---

