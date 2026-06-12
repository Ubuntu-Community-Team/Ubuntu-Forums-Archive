---
title: "networking issues from ubuntu 12.04 (inside VM) to gateway"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by jordanscanada on 2012-07-23
Hi all,

I have set up ubuntu 12.04 server in a VirualBox vm environment on a windows 7 host.  The VM is setup to bridge ubuntu on my network.

The problem is the network connection appears to be flakey.  I can ping the host from the VM and not lose any packets at all - when I try to ping the gateway from the VM however, I get 20 second periods every few minutes where the pings are not being returned.  

I read around and some users suggested dropping the MTU to 1492 from 1500 but it hasnt made a difference. 

Note that I can ping the gateway from the host and not lose any packets.  Similarly I can ping the VM from the host and the gateway and not lose any packets - the problem is only from the VM to the gateway 

Any ideas?

---

### Post by jordanscanada on 2012-07-24
Also,  I thought I'd add that the same issue occurs when I ping through the gateway to any location on the internet

---

### Post by jordanscanada on 2012-07-24
I ended up changing the vm engine from virtual box to VMware.  The problem still existed for a while and then it just corrected itself. I have no idea why

---

