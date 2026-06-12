---
title: "Access server from outside LAN via SSH"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by gacanepa on 2012-07-18
Hi all,
I have a home server running Ubuntu Server. This server is behind a router with a static IP.
To access the apache server, in the router I have redirected port 8888 (public) to port 80 (private) so when I type xxx.xxx.xxx.xxx:8888 (where the x's represent the router's static ip address) in a web browser from outside the LAN, it displays a home page. That works just fine.
Now I would like to access the ssh server from outside the LAN. To accomplish this, in the router I redirected port 1982 to the server's (private) port 22, but I keep getting a "Connection timed out" message in Putty while trying to connect to the server.
Some things to consider:
1) the sshd daemon is running on the server.
2) Iptables is not blocking any incoming connections (just to test, it's configured with an ACCEPT ALL policy).
3) The Putty connection is xxx.xxx.xxx.xxx:1982 (where the x's represent the same IP address as above).
4) I already checked linuxquestions.org/questions/linux-newbie-8/ssh-access-from-outside-the-lan-176986/ where a suggestion is given but I am not quite sure as how to implement it.
I hope I have asked this question the smart way. Any suggestions / ideas are more than welcome!

---

### Post by sanderj on 2012-07-18
On your LAN, can you access ssh on the server?

---

### Post by papibe on 2012-07-18
Hi gacanepa.

Just to make sure: Are you trying to connect to your server from outside the network, aren't you?

Just remember that accessing you public IP from inside your own network it is not usually possible.

Just a thought.
Regards.

---

