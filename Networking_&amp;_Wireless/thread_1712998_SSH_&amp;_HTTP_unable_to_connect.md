---
title: "SSH &amp; HTTP unable to connect"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by benholiio on 2011-03-23
I have an Ubuntu 10.10 machine hosting a virtual Windows machine on virtualbox. 

I have 3 servers I connect to using SSH with password authentication, on standard port (22)

For some unknown reason, I have one server that I cannot connect to Via SSH using putty/terminal or HTTP via Browser from my Host nix box, but my Virtual machine CAN connect via both. 

Same machine, same network, one virtual with a bridged adapter, one physical network card connected to my network.

Really not sure where to start in troubleshooting.

Any suggestions?

---

### Post by conneco on 2011-03-23
What output do you get from the terminal when you initiate the ssh connection?

---

### Post by deconstrained on 2011-03-23
```
ssh -vvv user@hostname
```
That could help with diagnosis.

---

### Post by benholiio on 2011-03-25
> **deconstrained said:**
> ```
ssh -vvv user@hostname
```
That could help with diagnosis.
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ssh.hostname.co.uk [xxx.xxx.xxx.xxx] port 22.
debug1: connect to address xxx.xxx.xxx.xxx port 22: Connection timed out
ssh: connect to host ssh.hostname.co.uk port 22: Connection timed out

---

### Post by slashwannabe94 on 2011-04-07
I get the same error. More research :D

---

