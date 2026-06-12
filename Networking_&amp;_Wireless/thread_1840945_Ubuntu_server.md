---
title: "Ubuntu server"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by negatelli on 2011-09-08
Hi,
im gona make a ubuntu proxy server.

any how im gonna try and make a server that limits the internet so that all pc's to the network get's a fair share of internet or Deny's the pc's internet if it try's to download illegal files ( bit torrent downloads )


any how its a must that it can handle atleast 50 computers...


any way i dont have any clue how to make that cind of server or any server at all...

so any tips of pre programed server os or apps i can get for free ?

---

### Post by wildmanne39 on 2011-09-08
Hi, here is two links for setting up a server I have never done it myself so the links are all the help I can give.
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
[https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html)
Thank you

---

### Post by SeijiSensei on 2011-09-09
You're in for a long period of research and testing, my friend.  You'll need to become good buddies with iptables, squid, and IP routing.

What you want to do is set up a "[transparent proxy]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html")" between the network and the Internet.  Typically that's done with a program called Squid.  Squid allows you to write rules, called "Access Control Lists" or "ACLs", that permit or deny access to remote objects based on the type of file being transferred.  You can write a rule that denies, e.g., .torrent files.

I'd also suggest including a rule on your firewall that blocks all traffic that originates on ports > 1023 within the network and is destined for similar high ports on remote machines.  Most legitimate traffic targets the "well-known" ports like HTTP's port 80, all of which are numbered from 0-1023.  Torrents, for instance, typically use high ports on both ends of the connection and are easily defeated by such a blocking rule.  In iptables it looks like

```
iptables -A INPUT -p tcp --sport 1024:65535 --dport 1024:65535 -j DENY
iptables -A INPUT -p udp --sport 1024:65535 --dport 1024:65535 -j DENY
```

---

### Post by HermanAB on 2011-09-09
Read the Advanced Routing Howto on tldp.org.

---

