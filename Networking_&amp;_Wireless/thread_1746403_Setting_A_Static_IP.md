---
title: "Setting A Static IP"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by TetraKill on 2011-05-01
I've been looking online for a while now, and I haven't been able to find out how to do it.  I have a Belkin f5d8635-4v1 modem/router, so I am connecting wirelessly.  I am on 10.10 at the moment.
Thanks.

---

### Post by poolet on 2011-05-01
sudo su
"your password"

ifconfig "**interface**" down
ifconfig "**interface**" *"*IP_address" netmask "***netmask**"* up
route add default gw "[I]**gateway_address**"

[/I]

---

### Post by TetraKill on 2011-05-01
What is the "interface"?

---

### Post by Iowan on 2011-05-01
> **TetraKill said:**
> What is the "interface"?

"Ordinarily" a wireless card would be wlan0 - but my laptop calls it eth1. From a terminal (Applications>Accessories>Terminal), **ifconfig -a** *should* show what interfaces are available.

---

### Post by TetraKill on 2011-05-01
Oh, thanks, I'll try it now.

EDIT: Thanks again, working now.

---

### Post by Iowan on 2011-05-01
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :D

---

