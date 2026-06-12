---
title: "Where should policy based routing rules live?"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by schickb on 2010-03-25
Seems like this should be a simple question, but I've looked around and have not found an obvious location to keep custom policy based routing rules in Ubuntu.

/etc/network/if-up.d comes to mind, but I was wondering is that was a "standard" spot. Also it doesn't seem like these rules really need to run each time an interface is up'ed or down'ed.

Commands that need to be run are things like:

ip rule add from 192.168.1.1/32 table blahblah
ip route add 192.168.1.0/24 dev eth1 table blahblah

---

### Post by byStanderone on 2010-03-25
...hope i get you right, iptable is handle by 'ufw' (uncomplicated firewall), and firestarter is its 'gui' for easy configuration.

---

### Post by schickb on 2010-03-25
> **byStanderone said:**
> ...hope i get you right, iptable is handle by 'ufw' (uncomplicated firewall), and firestarter is its 'gui' for easy configuration.

No, iptables is different. I'm talking about routing rules for iproute2.

---

### Post by byStanderone on 2010-03-25
...well, i'd guess it's stored in the router itself.

---

### Post by tc0nn on 2010-04-01
bump....

Anyone know the answer to this? 
I put mine in rc.local, but I assume there is a better place.

---

### Post by Keeper of the Keys on 2012-07-16
Better late then never....

As far as I know you stick those rules in /etc/network/interfaces in the stanza of the interface they deal with.

---

