---
title: "DHCP Server Hooks"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by btrichardson on 2009-02-20
Hello all,

I'm in the process of implementing a DHCP Server for multiple VLAN's I have configured in a lab environment.  I'm wanting to limit who can get a DHCP address for each VLAN based on the MAC address.  For example, I'd have a table of allowed MAC addresses for each VLAN.  I'd like this table to be in something like a PostgreSQL database so I can update it via a web interface.

Does the dhcp3-server have any hooks that can be called after a DHCP request is requested, but before an IP address is handed out?  I'm wondering if the server calls a particular executable script when this happens that I could use to query the appropriate database to see if the MAC is entered.  Thus, the server would have to pass to the script the MAC address in question, as well as the VLAN subnet it's connected to.

Any suggestions?

--
Thanks!
Bryan

---

### Post by kidders on 2009-02-21
Hi there,

You don't need to hook into a DHCP server to do that, really. Most are capable of controlling IP address assignment based on MAC address. Altering the access list (eg adding a new machine, or moving one from one subnet to another) would be a matter of modifying the server's config file & reloading it.

---

### Post by btrichardson on 2009-02-21
Hey Kidders,

Thanks for taking the time to respond.  I appreciate it.

So, from what you've said, I take it my best bet would be to set up some sort of cron job that accesses my database every so often, regenerates the DHCP config file, and reloads the DHCP server.  Correct?

--
Thanks again!
Bryan

---

### Post by kidders on 2009-02-22
Hmm... I would probably leave the database server out, tbh. Using cron to copy its contents into the DHCP server config file seems like an unnecessary extra step. If your web interface accessed the DHCP server config file directly, you could cut out two points of failure (cron & PostgreSQL), and having it reload the configuration itself would mean any changes could take effect right away.

You could either write the web interface yourself, or download something that already knows how to manipulate DHCP configurations (eg Webmin?). Either way, the biggest problem I have with adding PostgreSQL & cron to the equation is that if there were some kind of problem regenerating your DHCP configuration, the first you'd hear if it would be when the machines on your network mysteriously start assigning themselves 169.x.x.x addresses, and refusing to talk to each other. Personally, I'd much prefer it if the web interface could say "That hasn't worked. Try again.", rather than "Wait 5 minutes & see if your network is still there".

Either approach would work though ... so the choice is yours.

**Edit:** One other issue just occurred to me. Using a web interface that reads from a database would create problems if you ever modified your DHCP server configuration directly for some reason. For example, you'd have to watch for things like conflicting hosts/subnet configurations yourself, because manual changes would never be reflected in the web-based editor. The more I think about it, the less I like the idea of using cron/etc. What do you think?

---

