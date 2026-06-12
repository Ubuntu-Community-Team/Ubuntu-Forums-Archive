---
title: "Never seen anything like this is my life"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by nkae100 on 2011-03-17
... so I've forwarded incoming connections on port 25 to my virtual machine with the following commands:

> sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d 10.1.1.3 --dport 25 -j DNAT --to 192.168.56.101:25

sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.56.101 --dport 25 -j ACCEPT

The strange thing is the connections coming through in the virtual machine seem to be getting dropped. A port scan from the internet says the port is closed, but it is not the case as I can see the connection coming through.
As you've probably worked out, I am running a mail server. When I send myself test mail, the connections from the senders mail server also gets dropped.

Anyone ever had this experience before or has a clue whats going on?

---

### Post by sedawk on 2011-03-17
You can debug SMTP easily with telnet to port 25 as it
is a simple ASCII protocol.

E.g. try this first from localhost with target "localhost",
then with the IP, then from a second machine with IP or
hostname.
```

# telnet to port 25
telnet <localhost=127.0.0.1 or hostname or IP> 25
#now connection should be established and you can enter
EHLO<return>
# or HELO any_string <return>
# Press Ctrl-D to end connection properly

```

This might give you a better idea of where the problem is.
I do not recommend to do this with real SMTP servers.

---

