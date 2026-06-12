---
title: "SSH port 22....eh...you know the drill by now..."
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by j_cook on 2010-12-21
Alright, so it seems like everyone and their mother is having a port 22:connection refused problem with SSH. None of what I have read has been what I have been experiencing, so I figured I would post here. The worst that could happen is this gets completely ignored, or I am told that there is already a solution, that I missed it, and directed to it.

Here is my problem:

Just learned how to ssh into my machine a few days ago. Everything has been running smoothly until I ran into a little problem: all of a sudden I can't connect anymore.

I have sshd-server installed and updated. I have sshd turned on 
```
/sbin/service sshd start
```And I even ran:

```
/etc/init.d/sshd start
```Because I was told that it would start ssh from boot. Nothing has changed from today and yesterday and I haven't been having problems with port 22 being blocked.

I have also tried to ssh into the machine by the machine itself:

```
ssh <IP of machine>
```with the same error.

---

### Post by 3Miro on 2010-12-21
Do an
```
nmap localhost
```
this should show port 22 as open. You can also try to nmap from another machine to see if this is an issue with the port or ssh settings.

---

### Post by j_cook on 2010-12-21
Yeah I checked if was open a few days ago when I started and it showed that it was and I just checked again since you told me to and nmap says it is open still.

I restarted sshd:

```
/sbin/service sshd stop
/sbin/service sshd start
``` and I can now at least ssh into the ubuntu machine via itself, but I cannot ssh into other machines nor can I use other machines to ssh into it.

Both of the other machines (iMac and Fedora) have sshd properly installed.

---

### Post by 3Miro on 2010-12-21
Can you see the open port form other machines. It may be blocked by a firewall. SSH may also be configured to accept only local connections. (note sshd doesn't have to run on the guest, you only need ssh installed)

---

### Post by j_cook on 2010-12-21
The other machines are on my home network. Neither have a firewall blocking port 22. I wonder if I need to reset ssh on those machines (maybe try a reboot?).

---

