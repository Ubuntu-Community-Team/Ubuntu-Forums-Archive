---
title: "Unable to connect to specific OpenSSH daemon"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by Jochus on 2011-05-19
Hi,

I have this very weird problem: I'm not able to SSH to 1 specific server on the web. I can access everything, but not that specific server.

When I try to SSH, I get this:

[PHP]
$ ssh my_username@my_host
ssh: connect to host my_host port 22: Connection timed out
[/PHP]

When I reboot to Windows, I can SSH using Cygwin. I'm using Ubuntu 10.04 Lucid and OpenSSH client 1:5.3p1-3ubuntu6.
I tried sniffing the network with Wireshark, but I cannot understand why the TCP connection cannot be set up. I'm sure it's an Ubuntu problem as I'm able to connect to that server on the same machine, but different OS.

Who can help me out?

---

### Post by Jochus on 2011-05-19
Hmm, now I see every port to that specific server is blocked :-/ ... There's a webserver running on port 80 which I cannot contact!

I can ping the server, but every port on that server from my machine is blocked.

iptables is not active ... and it can't be the iptables of the server, as I have access when I reboot to Windows ...

---

