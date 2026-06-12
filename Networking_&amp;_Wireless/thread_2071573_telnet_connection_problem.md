---
title: "telnet connection problem"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by sergkrs on 2012-10-15
I have 2 computers in my home wired network: with Windows 7 and Ubuntu 12.04. I installed telnet on Ubuntu PC and ran an application that listens to port 4212. When I ran "netstat" I see that the port is open and I can connect to this port from Ubuntu computer itself using command "telnet localhost 4212". 
But when I try to open this connection from my Windows computer it fails although connection to standard telnet port works fine. 

Any idea what is wrong and how to resolve this issue?

P.S. Firewall is disabled on Ubuntu computer.

---

### Post by ahallubuntu on 2012-10-15
What client are you using on the Windows machine?  Have you tried downloading/installing the Putty client instead of using a built-in Windows client?

Also, is there a reason you prefer telnet to say ssh login?  Just wondering.

---

### Post by sergkrs on 2012-10-15
I used Windows built-in client as well as Putty, result is the same. I need this telnet connection to control the application I ran on Ubuntu computer.

---

