---
title: "SSH over LAN mystery"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by randomEE2 on 2010-11-01
I have a LAN set up, and would like to ssh into my desktop (IP address 192.168.1.102) from my laptop (IP address 192.168.1.104).  I have set up the ssh server on my desktop, and the following commands get me to a shell-within-a-shell on my desktop:

ssh localhost
ssh 192.168.1.102

All seems well.  However, running the second command from my laptop results in a long delay and finally the error message "Connection closed by 192.168.1.102".

Additionally, I should say that I have apache set up on my desktop, and entering 192.168.1.102 into a browser on my laptop shows the pages I have serving.

I am at a loss as to where to look next since:
Accessing the desktop via 192.168.1.102:80 seems to work from anywhere.
Accessing the desktop via 192.168.1.102:22 works from the desktop but not from the laptop.

Does anyone have any idea what might be going on here?

---

### Post by srhart on 2010-11-01
I have three rules I use when troubleshooting connectivity on PCs:
- check the logs
- look for firewalls (sometimes I've even found multiple software firewalls on machines) - I suspect this is the issue in your case (check 'sudo ufw status')
- shutdown, depower (yes depower - most motherboards dont remove power from NICs on simple restart) then restart the machine - this isnt as often needed on Linux as it is on Windows machines

Good luck
Simon
-------------------
[www.L3n.co.uk]("http://www.L3n.co.uk") L3n Network Support - Contact L3n for voice and data network design, supply, installation and support - based in Cambridge UK

---

### Post by randomEE2 on 2010-11-01
Thanks for the response!

Where should I look for the logs for this sort of issue?

I ran the ufw command.  It returned:
Status: inactive

Restarting with poweroff/unplug doesn't seem to have helped anything.

So, the logs seem most promising...

---

### Post by kimchi on 2010-11-01
I have no solution off the top of my head, but perhaps there is a network configuration issue with /etc/hosts or /etc/ssh/sshd_config (ListenAddress)? Might want to compare those files on both computers.

---

### Post by srhart on 2010-11-02
On your destination machine, try:
cat /var/log/auth.log* | grep ssh

You should see line(s) containing something like:
sshd[xxx]: Server listening on 0.0.0.0 port 22

This shows that the sshd server is installed and starting. If there's no such lines then try installing the server with;

sudo apt-get install openssh-server

Simon
--------------
[www.L3n.co.uk]("http://www.L3n.co.uk") L3n Network Support - Contact L3n for voice and data network design, supply, installation and support - based in Cambridge UK

---

### Post by SeijiSensei on 2010-11-03
Place an entry for the server in the /etc/hosts file of both the client and the server.

---

### Post by SlugSlug on 2010-11-03
```
sudo tailf /var/log/auth.log
```

on the server 

and 

```
ssh -vvv ip.to.server
```

on the laptop

---

