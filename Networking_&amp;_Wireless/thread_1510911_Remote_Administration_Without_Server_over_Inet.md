---
title: "Remote Administration Without Server over Inet"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by asdir on 2010-06-16
Hi everyone,

I'd like to administrate my parents' computer over the internet. When I google for a tutorial on what I have to install and configure on my and their PC, I always end up with tutorials on servers and the like or tutorials for a connection between Ubuntu and Windows.

Does anyone know of an easy tutorial for remote desktop when two private, simple (Ubuntu-installed) PCs are involved?

Thanks for any hint. :)

---

### Post by Blackbird_13 on 2010-06-16
Not sure if this is what you are after, but this is what I did.

Installed openssh-server and configured for Key-Based SSH Logins. See links below. I found the guidance clear and did not have any problems configuring - just be methodical.

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Set up Remote Desktop on dad's pc:

> System..Preferences..Remote Desktop
Ticked   "Allow other users to share pc" and "You must confirm each access"
Also set a password.Set up port forwarding (for ssh port 22) on my dad's router.

After checking that ssh and my keys worked (see above links), I logged in as follows:

In a terminal enter.
```
ssh -L 5900:localhost:5900 [dad's-ipaddress]
```Keep first terminal open and in another terminal enter
```
vinagre localhost:5900
``` You should be prompted for a password and once accepted you should have Remote Desktop access. I have a slow broadband connection so navigating around using Remote Desktop is pretty slow.

---

