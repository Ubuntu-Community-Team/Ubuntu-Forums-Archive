---
title: "ssh with reserved port and ssh-agent: how to?"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by KeesM on 2010-04-17
Dear all,

I am trying to set up an NSLU2 network disk with Debian Linux, to operate as samba server. This in itself works fine; what I have problems with is in accessing it safely over the internet via a SSH tunnel, using Ubuntu 9.10. To do so, I use SSH to forward port 445, and then mount a share using [FONT="Courier New"]-t cifs[/FONT].

What is my problem (as seen through the eyes of a relative beginner, non-english): to connect using port 445, I need to run SSH as root, e.g. using sudo, as port 445 is a privileged port. As long as I want to log in using a password, this works fine :) . However, when I want to log in using a key file/passphrase already loaded into ssh-agent, this breaks down as running ssh as root apparently blocks the access of ssh to the ssh-agent deamon :( ?

So, for good order:
[LIST]
[*]mounting via the SSH tunnel as root (sudo) works perfect as long as I use a password
[*]Logging in as user using SSH and key file/pass phrase via ssh-add/ssh-agent works great as long as I do not do this using sudo
[*]But combining these to forward the port (needing sudo) and use a key file (not allowing sudo) gives me a problem...
[/LIST]
And [FONT="Courier New"]sudo ssh-add[/FONT] can not access the running ssh-agent to add the key file as root

What is a clean way to solve this while using a key file approach? I can do it using a non-reserved port e.g. 12345 instead of the port 445 reserved for this purpose, but this does not feel right to me... or is this just me?

Any ideas?

---

### Post by Brandon Williams on 2010-04-20
> **KeesM said:**
> What is a clean way to solve this while using a key file approach? I can do it using a non-reserved port e.g. 12345 instead of the port 445 reserved for this purpose, but this does not feel right to me... or is this just me?

That is what I would recommend, even if you were going to continue to use password based login. If there is a simple way to avoid running a command as root, it's generally a good idea to do so, especially when the command is used for remote access of one sort or another. I always run ssh for my tunnels as a non-root user, which means that I always use non-standard local ports for standard services.

---

### Post by KeesM on 2010-05-14
Thanks. Indeed probably the best way to solve this, and I did not find any further issues (working great). Mounting cifs filesystem on this port was no issue.

---

