---
title: "How to get two networks with 2 NICs working"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by Shellbak3 on 2012-01-04
I have a specialty computer running Ubuntu 11.10.  I'm new to Ubuntu and LINUX.  The machine has two NICs, eth2 is 100 mbs and wired to a router.  The other, eth3, is 1000 mbs which I have wired to a switch.  The latter I want to use ONLY to connect to a Gigabit camera for control and image data.

If I enable eth3 then the computer chooses to use it to futilely attempt to connect to the web.  

How can I set up the two ports so that eth3 is only used for the camera?

Here's my interfaces file:

```

auto lo
iface lo inet loopback

auto eth2 eth3
iface eth2 inet dhcp
# router dhcp assigns 192.168.1.103

iface eth3 inet static
address 169.254.1.1
netmask 255.255.255.240
gateway 169.254.1.2
mtu 9000

```

---

### Post by Shellbak3 on 2012-01-04
OK, I found that removing the "gateway" line for eth3 which uses a static ip address works just fine.

---

### Post by Iowan on 2012-01-04
FYI... the "gateway" is where all non-local traffic is sent. I'm kinda curious what happened to eth0 and eth1 - but if it works...

BTW, would you consider the problem [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by Shellbak3 on 2012-01-05
The long story is that the computer, which will run headless on an aircraft when it is deployed, was delivered with the Gigabit NIC not supporting Jumbo Frames which was a "must have" and the CPU was slower and did not have two cores also a "must have", this was not as described by sales.  It took a long time to get this rectified and the machine returned.  I've spent several days trying to get it working as needed and have looked at the files /lib/udev/rules.d/75<persistant net> and /etc/udev/rules.d ... (I'm home and can't remember the exact names).  Both are auto generated and this results in the rules.d file having the old eth0 and eth1 as well as eth2 and eth3.  I suspect that eth0 and eth1 are on the MB so the vendor had to add a board with new NICs.  So the machine probably has 4 NICs only two of which have physical ports.  (Or there's yet another file I don't know about!) I would prefer eth0 for what will be an intranet contained in the aircraft with 4 or 5 computers and eth1 for the Gigabit LAN local to each machine to connect to sensors.

Something did happen in all my experiments, though, eth2 and eth3 were associated with addresses that ended in 80 and 81 but suddenly are have address association swapped (at least now in the order I prefer).  I don't know why and am worried that it might swap again.  

If it boots correctly when I get to work I'll consider the question answered - and then ask another!

---

