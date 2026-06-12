---
title: "IPtables, firestarter, site blocking..."
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2009-06-21
So I've got a list of 16,000+ advertising sites I'ld like to block and am working on the best way to do this.  I've discovered that firestarter is just a GUI for IPtables so I'ld like to remove it.  IPtable manipulation for me is going to take a bit more reading but I'ld like to know if given a text file of fqdn's can a script be written to make IPtables block incoming packets from those sites???

The only hitch to my plan so far is keeping the list updated.  I suppose if a site is found that maintains a list wget could be used in conjunction with cron to make this job a script and forget one.

Any input anyone???

Thank You,
Barrie

---

### Post by dmizer on 2009-06-21
Use GUFW instead of Firestarter. It's a GUI for "uncomplicated firewall". It's fairly simple to use.

However, to block sites, all you have to do is send the blocked site to localhost in /etc/hosts like so:
```
127.0.0.1 localhost [COLOR="Red"]advert-site1.com advert-site2.com advert-site3.com[/COLOR]
127.0.1.1 tsubasa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Barriehie on 2009-06-21
> **dmizer said:**
> Use GUFW instead of Firestarter. It's a GUI for "uncomplicated firewall". It's fairly simple to use.

However, to block sites, all you have to do is send the blocked site to localhost in /etc/hosts like so:
```
127.0.0.1 localhost [COLOR="Red"]google-analytics.com advert-site1.com advert-site2.com[/COLOR]
127.0.1.1 tsubasa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I think ufw has an issue, it would never enable and always said ERROR: / world is writable or something to that effect.  I think I can do this via a script that will read my block-these-sites.lst file.

```

iptables -A INPUT -s <line from block-these-sites.lst> -p http -j DROP

```

---

### Post by dmizer on 2009-06-21
Well, if you must do this with IPtables, then perhaps you will be intested in this: [http://www.netfilter.org/](http://www.netfilter.org/)

---

### Post by Barriehie on 2009-06-21
Good link dmizer!  Thank you!

Barrie

---

### Post by dmizer on 2009-06-21
Another easier alternative with automatic updating would be to squid with the [dansguardian](http://dansguardian.org/) plugin. Both squid and dansguardian are in the Ubuntu repos.

---

### Post by Barriehie on 2009-06-21
> **dmizer said:**
> Another easier alternative with automatic updating would be to squid with the [dansguardian](http://dansguardian.org/) plugin. Both squid and dansguardian are in the Ubuntu repos.

Thank you, I will look into that.

Barrie

---

### Post by Brandon Williams on 2009-06-21
I recommend against doing this with iptables rules. 16,000 unique addresses that can't be easily reduced to a smaller set of subnets is quite a lot for iptables. It will take a long time at boot to load such a large list of rules (several minutes on some machines), and having 16,000 unique addresses to check for every outgoing packet could impose unacceptable overhead on good packets, which have to be checked against the whole list. A request-based filter, like Firefox's Adblock Plus or the suggested Squid plugin, will be much better in terms of their overall impact on the connection, since they only have an impact when the initial request is processed, not throughout the life of the connection.

If you must use iptables instead of the other options, then I recommend that you create a tree of rules using ipset, with one level in the tree for each octet in the ip address. My own experimentation indicates that this will impose much lower per-packet overhead (both for average and worst-case) than your list of 16,000. This would be improved even more by making the root of your tree a rule that only matches on TCP SYN packets, since it would limit any significant overhead to connection initiation and not penalize good connections throughout their lifetime.

In addition, I don't think you want to drop the incoming packets, since that will mean that your machine has overhead associated with waiting for those connections to time out. Instead, you want to watch for outgoing SYN packets (use the iptables '-p tcp' and --syn options) and respond to them with TCP reset packets (use the iptables '--reject-with tcp-reset' option). This would mean that you don't have to wait for TCP's retransmit timeout before your system gives up on the connections.

---

