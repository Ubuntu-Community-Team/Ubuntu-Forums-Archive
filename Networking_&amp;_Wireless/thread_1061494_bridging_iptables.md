---
title: "bridging iptables"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by sinclair86 on 2009-02-05
Ok originally I wrote this wrong I guess. Here is what I am trying to do I have my xbox bridged to my xubuntu computer using bridge-utils. The first thing I am running into is I am getting a moderate NAT error when I do a test xbox live connection. I have a the xbox set to a static ip 192.168.1.10 and eth0/eth1 are bridged to br0 dhcp and has the ip address of 192.168.1.6. I have the ports opened on my router. Is this a routing table issue or a iptable thing. Second iptables. What I want to be able to do, again (switched from windows to linux cause I hated how slow), is be able to drop people from my games. So the thing here is how do I accept all traffic from a certain ip or range of ips with ip tables and then block everything else.

---

### Post by sinclair86 on 2009-02-08
bump

---

### Post by superprash2003 on 2009-02-08
do you want to share an internet connection using your ubuntu machine as router?>

---

### Post by sinclair86 on 2009-02-08
I have 2 nic cards one to my router and the other to my xbox Im trying bridge the connection and then have a firewall between my xbox and the bridge

---

### Post by superprash2003 on 2009-02-10
you could try firestarter or ufw.. if not [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by sinclair86 on 2009-02-10
Trust me I like to do my homework before I come here because its always so hard to get a decent reply to something that stumps me. the problem here is when the connection is bridged or I have ICS (done both) and I add XBOX Live IP range as to alway allow connection when I toss on the firewall for about a minute I get signed off.

---

