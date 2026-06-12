---
title: "How to use NAT for accessing via SSH?"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by mamboknave on 2013-08-30
I had great support from this forum for my [previous help request]("http://ubuntuforums.org/showthread.php?t=2171025"). I'm back for the next steps.

Objective: I need to ssh/sftp my computers from remote in a manner more secure than what I'm doing now.

I've a router which works as gateway and two computers connected to it.

Currently, I'm doing ssh through the gateway IP address (say 12.345.678.90) while defining the forwarding port to select the proper computer. For instance:

> ssh -p 122 12.345.678.90

As I was told that doing so is very insecure, I'm here asking what should I do instead and how to configure the router/computers.

Of course, before posting here I did google the matter receiving very unclear (to me) info. Yes, I know nearly nothing about networking.

Looking fwd to receiving some help again. Thanks!

---

### Post by Lars Noodén on 2013-08-30
SSH is quite secure, unless you use a bad password.  You can eliminate the chance of guessing the password by turning off password authentication and using keys instead.  As far as accessing from outside, your router has to be set up to forward an outside port on the WAN to a local port on a machine on your LAN.  The specifics vary from router to router and model to model.  But most, if not all, allow such port forwarding.  Log into your router as admin (or whatever it is called there) and look for port forwarding or port mapping.

---

### Post by houstonbofh on 2013-08-30
If you look in your logs, you will se a LOT of people trying to log in to your server via ssh.  If you have an easy password, and username you are wide open.  Of course, half of them are trying root, which Ubuntu does not have...

That said, fail2ban is a very nice utility for stopping script kiddies.

PS:  Some people also like to use non-standard ports for ssh.  I think they also still use bicycle helmets. :)  To each his own.

---

### Post by SeijiSensei on 2013-08-30
> Some people also like to use non-standard ports for ssh. I think they also still use bicycle helmets

In general I use iptables rules to limit the IPs that are allowed to connect via SSH.  I do use one high port that is publicly visible, but that connection uses a shared key rather than a password.

And, yes, I also use a bicycle helmet.

---

