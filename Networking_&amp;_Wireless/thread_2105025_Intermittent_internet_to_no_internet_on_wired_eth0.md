---
title: "Intermittent internet to no internet on wired eth0"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by deadgoon on 2013-01-14
I'm trying to get consistent access to the internet on my Ubuntu 12.10 AMD_64 machine. Right now the connection is completely down, but sometimes it works.  I am typing this on my Windows machine and all information is from memory since I can't post from Ubuntu.

I'm connecting using a wired connection.  The connection works fine while booted into Windows, but is intermittent to non-existent while booted into Ubuntu on the same machine.

I've tried updating the drivers, but that doesn't seem to have any effect of the problem.  (Chip is the Realtek 8168, I've also used a wireless USB dongle, but am experiencing the same problem).  I've also tried messing with my MTU setting, but that only seems to make it worse (i.e. no connection at all).

Is anyone else seeing this problem?  What further information can I provide?  What further steps can I take?  I really want to get this working.

---

### Post by deadgoon on 2013-01-15
Okay, looks like I solved this one on my own.  For some reason Ubuntu was choking on my ISP's DNS servers.  I noticed this by pinging google.com and then pinging it's IP address.  I wasn't getting anything from google.com, but the IP was pinging like a champ.  I added Google's free DNS servers to my IPv4 network configuration and everything is cool.  Details below:

-Click on network icon in top bar
-Click on Edit Connections
-Select network connection and click Edit...
-Select IPv4 Settings tab
-Enter DNS servers in the Additional DNS Servers text box, separate by comma (ex. 8.8.8.8,8.8.4.4  This will give you Google's DNS servers)

--->EDIT:  Turns out this only worked for a few minutes, then right back to the same issues.  The REAL solution was in comment #4 in the thread listed below:

[http://ubuntuforums.org/showthread.php?t=1972984](http://ubuntuforums.org/showthread.php?t=1972984)

---

