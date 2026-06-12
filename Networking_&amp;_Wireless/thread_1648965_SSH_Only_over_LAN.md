---
title: "SSH Only over LAN"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by EnigmaticCoder on 2010-12-19
How can I only allow ssh connections over LAN and refuse connections over the internet?

---

### Post by spiky001 on 2010-12-19
You would have to enable it to go over internet, I use gufw and set it for incoming deny then set rules for ip I let ssh in

---

### Post by EnigmaticCoder on 2010-12-19
SSH doesn't have a built-in way to do that? How do I know if gufw is actually working?

---

### Post by spiky001 on 2010-12-19
I have also changed the default port number, scan your pc from here [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by slooow on 2010-12-19
You change the /etc/hosts.allow and /etc/hosts.deny files.
In hosts.deny you write:
```
sshd: 0.0.0.0
```
In hosts.allow you write:
```
sshd: 192.168.1.
```
or whatever your LAN network is called.
See man hosts.deny for more details.

---

### Post by tgalati4 on 2010-12-19
If your router has a built-in firewall, then you can only ssh via the internet if port 22 is port-forwarded to your local IP address for the machine running the ssh server.  Otherwise, ssh attempts from the outside will be blocked.  You can ssh on your local area network without problems, unless you are running a software firewall (iptables, gufw, etc) on any machine that blocks port 22.

If you change the default ssh port from 22 to something else, then you need to specify that port when you try to initiate an ssh session, or set it up in the ssh configuration files.

---

