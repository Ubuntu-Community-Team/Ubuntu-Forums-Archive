---
title: "SSH File Server?"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by Black Razor on 2009-03-18
I would like to set up my 8.10 desktop so that it allows me to access files from any machine via the internet.  I believe I use SSH for this, but have no clue how to set it up or use it.  I just need some easy to follow tutorials if anyone knows of any, and some advice if you have any.  I ideally want to be able to just access my files on the desktop from both my Vista laptop and my UNR laptop.

I have a strong technical background, so a relatively easy to follow tutorial will probably be fine. Thanks in advance.

---

### Post by lykwydchykyn on 2009-03-18
> **Black Razor said:**
> I would like to set up my 8.10 desktop so that it allows me to access files from any machine via the internet.  I believe I use SSH for this, but have no clue how to set it up or use it.  I just need some easy to follow tutorials if anyone knows of any, and some advice if you have any.  I ideally want to be able to just access my files on the desktop from both my Vista laptop and my UNR laptop.

I have a strong technical background, so a relatively easy to follow tutorial will probably be fine. Thanks in advance.

On the server, just install openssh-server.  Since you're opening it to the internet, I'd suggest the following additions:
 - install fail2ban
 - change the port from the default (weak move, but keeps the bots away)
 - limit the users to only the ones who need access
 - If you ONLY plan to access from these two clients, use private key authentication in place of normal password authentication

Instructions for most of the above can be found here:
[http://blog.dbugs.org/2007/08/29/ssh-security/](http://blog.dbugs.org/2007/08/29/ssh-security/)

On the vista laptop, you just need to install winscp.  
For the UNR machine, you can install sshfs to mount the remote ssh shares.  I am sure GNOME has a way to browse the ssh server in Nautilus, but I don't know how (using KDE here; I just type fish://hostname into konqueror to browse SSH).

Hope that helps.

---

