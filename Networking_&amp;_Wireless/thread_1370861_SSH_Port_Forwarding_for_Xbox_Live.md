---
title: "SSH Port Forwarding for Xbox Live"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by kirgy on 2010-01-02
Hi there, sorry if this is the wrong place to post im pretty new to the forums.

Basicaly, Im trying to get around a blocked port (tcp 3074) on the local network. I have found that SSH is the way to go by following some helpful threads that ultimatly lead me here:[ SSH Tunneling]("http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall")

Im running ubuntu 9.1 on my laptop, and ive got a virtual private server of my own with full SSH access located across the country somewhere. Ive manged to forward port 9999 via my VPS to allow internet access on my local machine, so I know i must have the requirements in place. The command I used for that was (removing real details obviously):

ssh -ND 9999 123.123.123.123 -l usernameForVPS
passwordForVPS

So want I want to do is forward the port on my local machine [3074] to my VPS, then the VPS use port 3074 to commuinicate with the xbox server. Just simply to bypass the blocked port on the local area network.

I know a lot of people's reactions will be "are you sure you are allowed to do this??", and yes I am. I've been given all appropriate permission to do it by my tutor and the college administrator. The reason the administrator wont unblock it is plain and simply - he doesn't know how (so much for meeting job qualifications eh?).

Any help will be appreciated,

---

