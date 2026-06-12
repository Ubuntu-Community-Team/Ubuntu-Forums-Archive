---
title: "ssh can't connect"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by zalberico on 2009-09-18
Hi,
I have two laptops and am trying to set up a simple server I can ssh into with my other laptop.  The server laptop is running 8.10 and the client is running 9.04.  I have ssh installed on both machines it works to get into my school's systems, but I cannot access my laptop running the server from my other laptop.

-The server laptop can access itself using ssh

-The ssh works on both laptops for connecting to an external server

-The output I get when running 'ssh user@ip -v' is:

debug1: Connecting to ip port 22
debug1: applying options for *
connection timed out

---

### Post by SoftwareExplorer on 2009-09-19
This might be obvious, but make sure firewalls or NAT aren't blocking port 22. If that was the case, it would be likely that it would be set up so the ssh out from a computer would work, but in would be blocked. Are the computers on the same LAN? If so, then it most likely rules out NAT problems.

---

### Post by pdc124 on 2009-09-19
from each machine do 
sudo nmap -sS ip.of.other.machine
 then can you 
sudo telnet ip.of.other.machine 22

---

