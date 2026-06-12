---
title: "ssh"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by tufu5 on 2011-05-26
I am trying to connect to another computer on my network using ssh but it's just not working. I type into the terminal:

ssh -p 5900 andy@192.168.0.3

but nothing actually happens, I also tried this:

ssh -vvv -p 5900 andy@192.168.0.3

and get this response:

daniel@desktop:~$ ssh -vvv -p 5900 andy@192.168.0.3
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.3 [192.168.0.3] port 5900.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug1: identity file /home/daniel/.ssh/id_rsa type -1
debug1: identity file /home/daniel/.ssh/id_dsa type -1
debug1: ssh_exchange_identification: RFB 003.007


I get nothing after that final line, does anyone know what the problem is?

---

