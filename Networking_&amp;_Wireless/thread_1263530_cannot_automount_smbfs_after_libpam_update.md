---
title: "cannot automount smbfs after libpam update"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by yens on 2009-09-11
Hi all,

We have ubuntu 8.04 server machine in the office, which shares home and public dirs via samba. I'm the only one running ubuntu 9.04 desktop but i also use samba to access the shares.
I made two entries in the /etc/fstab in order to auto-mount the shares. Everything was just fine till the moment I've updated the system with last updates (I think these were related to libpam).
The annoying thing is that the two shares have stopped mounting at start up.
The entries in fstab should be OK because after *sudo mount -a* command form the terminal the shares mount as before.
Could sm give me a hint how to solve this annoying problem.

---

### Post by yens on 2009-09-14
I shall answer to my own post because I found the solution for my problem. I'm very sorry and I fell like a complete noob cause I blamed the libpam update by mistake.
So, what was wrong from my point of view.
I've remembered that I defined a wired network in the network connections manager (set for DHCP) and after this I've noticed the problem with the fstab auto mount. 
Actually in the office I use the wireless card to connect to the network and respectively we don't have any wired network available.
I suppose that the script that loads the network shares at start up checks if the defined network(s) is(are) available and then loads the fstab entries.
What I did, was to delete all entries related to my eth0 card, also the entry in /etc/network/interfaces and voila!!!

---

