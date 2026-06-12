---
title: "Nmap and Access Point"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by Davh on 2012-02-07
I have an access point already configured (with another AP and it's 3 IP cameras) and I can get in with a WinXP laptop (by AP's IP address) who is wired connected, directly to the AP.

Now, I want to mount an Ubuntu computer to stay connected as my laptop is. There is not any difference, only OS.

First of all, I was trying to get in the AP (via browser and AP IP addr) like this:

AP and Ubuntu desktop connected to a switch, and this connected to a router (The IP address of the AP is static). With this, I can't get in to the AP. Even so, writing in terminal nmap -A -PN 192.168.1.123, I get this: "Nmap done: 1 IP address (1 hosts up) scanned in 201.64 sec"

With this, I understand that my computer CAN see the AP right :O?

PD: Doing this with my computer connected directly to the AP via eth cable it's the same thing.

Thanks!

Diego V.

---

### Post by Doug S on 2012-02-18
The "-PN" option for nmap by-passes host detection and forces namp to think the host is up. That namp says "1 host up" can be somewhat misleading. Example:```
doug@test-smy:~$ nmap -A -PN 209.121.21.186
Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-02-18 14:30 PST
Nmap scan report for 209.121.21.186
Host is up.
All 1000 scanned ports on 209.121.21.186 are filtered
Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 206.04 seconds

```For this example my router at 209.121.21.186 was turned off and the WAN network cable was unplugged. (I was coming from 209.121.21.192).

---

