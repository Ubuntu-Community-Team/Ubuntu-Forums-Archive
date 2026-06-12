---
title: "help with ssh ( timed out)"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by tragody on 2011-10-03
I used to do calculation with a server in Sweden while I am in US. Now I come to France and I could not use the server I was previously using to do my calculation. Every time I try to connect to it, it says "port 22 time out" blablabla

I kind of know where the problem is, because in US I use a LAN and here I am using the wifi in our university (they only have wifi, no matter in dorm or teaching building). so maybe the router doesn't know to whom it will send the incoming data. 

Any suggestion???

This is the information it shows if I use ssh -vv

han@ubuntu:~$ ssh -vv -Y [EMAIL="xyz@server.com"]xyz@server.com[/EMAIL]
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to server.com [xxx.xxx.xxx.xx] port 22.
debug1: connect to address xxx.xxx.xxx.xx port 22: Connection timed out
ssh: connect to host server.com port 22: Connection timed out

---

### Post by Doug S on 2011-10-03
Maybe the university does not allow outgoing connections to be made to port 22. Many companies do not allow it.

---

### Post by tragody on 2011-10-03
hey !!! thank you very much!!! But what can I do ? Change to another port???

---

### Post by Doug S on 2011-10-03
Someone else might have further or better input, but I would: First, confirm with the university if outgoing connections to port 22 are indeed not allowed; If not, then ask if some other port can be used to make an SSH connection to your server in Sweden; If yes, then set up your server in Sweden to listen on that port. However, if the university policy is to not allow outgoing ssh sessions, then you have to abide by it.

---

### Post by azmyth on 2011-10-03
Are you trying to connect from the same PC you had in Sweden? If no, then I'd also check your local PC to make sure your firewall isn't blocking you from connecting out. If still no, then changing the port in Sweden will probably be needed.

---

### Post by Dangertux on 2011-10-03
You mentioned it's for calculations, are they academic in nature? If so you might be able to ask the University administrators nicely to allow you to connect if it is them blocking port 22.

Just a thought.

---

