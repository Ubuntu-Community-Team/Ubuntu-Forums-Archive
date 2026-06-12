---
title: "ssh question"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by HypNemes on 2010-10-05
Hello all

I am very new to linux/ubuntu and am learning steadily.
Decided to try and stick with ubuntu.

I'm wondering though if ssh is fully installed as default with basic iso ubuntu-10.04.1-desktop-i386.iso ?

I tried to do a sshd-generate to generate some keys etc and I got an invalid command error.

But ssh is there as I can connect to other comps running it.

What does this mean?
How do I sort my keys out etc.

Im assuming i just have a basic ssh client instaleld and the sshd isnt installed yes?

Hyp

---

### Post by amauk on 2010-10-05
Install openSSH Server
```
sudo apt-get install openssh-server
```

---

### Post by pricetech on 2010-10-05
You can also install it via Synaptic.

---

### Post by HypNemes on 2010-10-05
ok thanks folks :)

Got them installed - just need to figure out how to stop them all from starting at boot lol.

Id like to be able to just boot and then start the servers/daemons when and if I want to..

Dont like the idea of booting and having laods of servers starting up..

All help is appreciated thanks :)

Hyp

---

### Post by dtfinch on 2010-10-05
Two ways I can think of to disable it:
Remove all the per-runlevel startup links:```
sudo update-rc.d -f ssh remove
```
Or make the startup script non-executable:```
sudo chmod 644 /etc/init.d/ssh
```I can't guarantee it won't get reenabled the next time you install updates to openssh-server.

I never thought of sshd as being a resource hog, but more of a necessary component of any server. If you want the best of both worlds (services available, but not running until you actually use them) you can install either xinetd or openbsd-inetd and configure them to run on-connect from there. Looking at one of my servers, sshd is using 1000 kb, and inetd is using 548 kb.

---

### Post by SeijiSensei on 2010-10-06
If you're worried about the security implications of running sshd all the time, here are three things you can do to help lock it down:

1)  Add rules to iptables that restrict access to port 22 to only IP addresses that you trust.

2)  Edit sshd_config and disable root logins.

3)  Edit sshd_config and disable password logins; rely entirely on shared keys.

---

### Post by amauk on 2010-10-06
also, install either denyhosts or fail2ban

These are daemons that monitor /var/log/auth.log
nd if they detect any suspicious activity (brute forcing your SSH account, for example), will ban the IP address from further connections

---

### Post by HypNemes on 2010-10-06
Hi once again.

Thanking you for the continued support.

I decided to go with denyhosts - seemed simple enough.

However...

I managed to install fine - edited the config file etc; but denyhosts just will not start.

Ive even installed chkconfig and added a symbolic link to init.d.

Ive chown and chmod the "daemon-control" file so tis executable - and tried and tried and tried "sudo daemon-control start" and it just wont!

All I get is..
daemon-control: command not found.

Even when I'm in the directory were "daemon-control" is and try executing it - it wont execute.

In chkconfig denyhosts is listed but as "off".

Any help is appreciated, thanks.

Hyp

---

