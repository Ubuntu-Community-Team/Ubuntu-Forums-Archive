---
title: "Network is fine, Can't access Internet"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Korniko98 on 2006-06-10
Hi, I recently installed Dapper as a daul boot with WinXP. On WinXP I can access both the network and the Internet perfectly.
On Dapper, the network is working fine, I can see other computers (which are connected to a hub which in turn is connected to a router) and can access shared files, but I can't access any websites using Firefox nor can I ping any external location. When I type a URL in Firefox it immediately shows me a "Problem Loading Page", but when I disconnect the ethernet wire it simply keeps looking for the host forever. I have looked through the forum and tried many different solutions (IPv6, blacklisting tulip, networking restart, changing pipelining in Firefox, messing with static IP and DHCP). I am quite new to linux and learning as I go along.

What outputs are necessary for someone to help me with this?

---

### Post by pnael on 2006-06-10
At least we need the output of :
ifconfig -a
route -n
cat /etc/resolv.conf

---

### Post by jvictor on 2006-06-11
U maybe running IPV6, using DHCP and not using a proper DNS server add

in addition to what pnael said, can u post the o/p of 
less /etc/hosts

---

