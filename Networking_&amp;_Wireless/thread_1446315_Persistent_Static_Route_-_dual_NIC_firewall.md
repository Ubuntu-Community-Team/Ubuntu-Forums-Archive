---
title: "Persistent Static Route - dual NIC firewall"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by pneumatic on 2010-04-03
I have a dual NIC firewall and everything works fine but only if I run the static route for the default gateway manually:

route add -net 0.0.0.0 netmask 0.0.0.0 gw x.x.x.x dev eth1

Where eth1 is my WAN interface and x.x.x.x is my WAN IP.  I've spent about 20 hours trying to figure out just how to get this static route to come up automatically upon reboot.  I've read all the manuals and all that jazz.

HELP ME PLEASE!

I've added the "up route..." or the "post-up route..." commands to the /etc/network/interfaces file but that does not work (although my other static routes work just fine from here).  I've copied the relevant text and pasted it onto the command line to confirm correctness - everything with the command is fine.

I've also creates a static-routes file (and chmod +x, confirmed the correct permissions, etc) in /etc/network/interfaces/if-up.d/ and attempted to set the routes here (yes - using the "/sbin/route add -net..." terms that work FINE from the command line).  But that does not work either.

So I have the correct command that works fine from the command line.  

HOW can I run it upon boot?

---

### Post by Iowan on 2010-04-04
I presume you've already tried adding **gateway x.x.x.x** to the eth1 definition in */etc/network/interfaces*...

---

