---
title: "Can't connect to certain HTTPS servers"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by Carl Foxmarten on 2013-07-09
It's weird, and rather confusing.

In the last three weeks, I've suddenly been unable to connect to certain secure websites, while others remain unaffected.

I can access the unsecured versions, but accessing the secured versions (on the exact same server! By IP address) results in "Connection Refused", no matter what method I use.
(so far I've tried Google Chrome, Firefox, and wget)

Servers that I cannot access:
[https://steamcommunity.com/](https://steamcommunity.com/)
[https://playtest.easports.com/](https://playtest.easports.com/)

Servers that I can access:
[https://www.inbox.com/](https://www.inbox.com/)
[https://www.youtube.com/](https://www.youtube.com/)

Any suggestions on what went wrong?
I'm using XUbuntu 12.10.

---

### Post by imlepid on 2013-07-18
Very interesting indeed.  Especially the wget part.

I strongly suspect that something in the path is causing the trouble and interrupting the connection.  Are you accessing this from work (where there might be some filtering device in the way)?  Do you have a proxy server configured?

If this is a laptop with wireless, try taking this to a coffee shop or somewhere with a public wifi hotspot.  If that succeeds then it confirms that something is blocking your original connection.

Also, try connecting using telnet to port 443 of a non-working server (and, for good measure try to a working one too).  Here's an example:
```

$ telnet playtest.easports.com 443
Trying 159.153.9.51...
Connected to playtest.easports.com.
Escape character is '^]'.
^C

Connection closed by foreign host.

```

Hope that helps.

---

### Post by Carl Foxmarten on 2013-07-18
Turns out, annoyingly enough, that the problem was entirely the fault of IPTables.

The key was the fact that attempting to ping the server in question resulted in a "[destination port unreachable]("http://www.linuxquestions.org/questions/linux-server-73/ssh-ping-and-destination-port-unreachable-716183/")" error, which is rather unusual.

Asking for IPTables' routing list gave me a weird list that I didn't know much about, but following [this guide on help.ubuntu.com](https://help.ubuntu.com/community/IptablesHowTo#Disabling_the_firewall) for disabling IPTables completely fixed the problem.

To make it permanent, I uninstalled IPTables and rebooted.
I probably should have tried more carefully to see what the firewall was trying to do, but because I'm already behind a firewall, I just removed the annoying one.

---

### Post by Carl Foxmarten on 2013-07-18
...And adding one more post so I can actually mark this thread as Solved. Which it totally is.

---

