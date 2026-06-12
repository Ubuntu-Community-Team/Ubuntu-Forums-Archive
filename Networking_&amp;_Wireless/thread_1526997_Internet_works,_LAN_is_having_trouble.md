---
title: "Internet works, LAN is having trouble"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by randomn00b on 2010-07-08
Hi - I'm new to linux.  I've tried to be responsible and search through the threads/google, but I'm not even sure of the right search terms to describe this problem.  It has honestly got me stumped.  Here's the behavior:

On the LAN we've got a linux box and a windows box.  Internally, the ubuntu 10.04 server box is fixed at 192.168.1.200.  The windows box is on dhcp, but presently at 192.168.1.202.

Cannot ping from one to the other, cannot ssh using Putty to the linux box.

Only here's the twist: I've got dyndns set up on the ubuntu box, and port forwarding on the router from 1234 to 22.  So when I ssh from the windows box to hostname.homelinux.org:1234 no problem, connects just fine.  Weird right?  And when I use the external IP address with port 1234 it works just fine.

Here are some even more confusing (at least to me) observations: I reboot the linux box, and after it boots back up, I can - for a little while - ssh to 192.168.1.200.  Wait a bit though, and it goes back to the usual behavior.  Equally strange: I reboot the windows box, same deal.  Initially, I can ping both machines from each other, ssh - everything is fine.  But wait a bit, and it goes back to acting as if neither machine is on the local network.  Router can see both however, and I can ssh using the external ip address.  Both connect to the Internet no problem.

Any ideas on where to even search for this?  I type in things like "no route to host", but all I see are the usual problems with firewalls.  I don't think that's what's going on here.

---

### Post by randomn00b on 2010-07-08
The rebooting leading to the LAN working may be a red herring.

Without rebooting, I caught it working again.  However, as I kept observing it, pings could be as high as 1000ms in latency.

So...  I'm thinking the router?  Anyone seen this behavior before?

---

