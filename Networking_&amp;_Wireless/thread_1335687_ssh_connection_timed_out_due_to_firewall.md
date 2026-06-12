---
title: "ssh connection timed out due to firewall"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by dantonic on 2009-11-23
Hello, just spent a few hours trying to figure out how to solve this.

After upgrading to Ubuntu 9.10 from 9.04, I was unable to ssh into my desktop from my other devices.

After trying a lot of stuff, I realized that disabling the firewal with 
sudo ufw disable
would fix the problem.

I came upon this [page]("https://help.ubuntu.com/community/IptablesHowTo") which provided the solution, without forcing me to disable the firewall.    Allowing ssh on the firewall with this command line:

  sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT

Just thought I'd share this solution.

---

### Post by Lars Noodén on 2009-11-24
You may also want to look at --limit.  See #3 in this:
[http://linuxgazette.net/108/odonovan.html](http://linuxgazette.net/108/odonovan.html)

---

### Post by dantonic on 2009-11-24
Hmm I've noticed that after a restart of the system I no longer am able to ssh unless I run the command again.  
Is there a way to make this permanent?

---

### Post by Lars Noodén on 2009-11-25
Right.  Your changes go away unless you set them to reload on start up.  Find where the firewall rules are stored, make a copy, then add your changes.  Then when the rules are reloaded, your changes come with them.

---

### Post by dantonic on 2009-11-28
> **Lars Noodén said:**
> Right.  Your changes go away unless you set them to reload on start up.  Find where the firewall rules are stored, make a copy, then add your changes.  Then when the rules are reloaded, your changes come with them.

looks like all I needed was to allow some ports on the firewall with

sudo ufw allow 22
sudo ufw allow 5900  //this one so I can use VNC as well.

---

### Post by Lars Noodén on 2009-11-29
> **dantonic said:**
> looks like all I needed was to allow some ports on the firewall with

sudo ufw allow 22
...

Excellent. 

Remember that the protocols that VNC uses are insecure so unless you want to open up more than you think you are opening you might want to tunnel it over SSH and block the non-SSH ports.

So if you tunnel over SSH, then use your VNC client to connect as before, but instead of connecting to a port on the remote host, connect to the port on the local host that is being tunneled to the remote host.  

```

# Tunnel vnc display :1 on the client to the server
# on the client:
ssh -L 5901:localhost:5901 server.example.org

```

```

# in another window on the client connect to the tunneled VNC:
krdc localhost:1

```

---

