---
title: "Starting vnc at boot, before login screen (gdm)"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by ivolution on 2010-12-27
I've a home server Ubuntu 10.10 and I want to make a connection to it without being physically at it.

It works, via my mac but ONLY when logged in.
I can't find a way to start vino before the login screen appears.

This server also acts as mediacenter so another x is not an option.

Any ideas?

---

### Post by cariboo on 2010-12-27
Enable auto-login?

---

### Post by ivolution on 2010-12-27
thanks for your reply

I don't want the data being unprotected.. there must be at least a password at login..

---

### Post by cariboo on 2010-12-27
Unfortunately, VNC/remote desktop, won't work unless you are logged into the remote system. Another option is to use ssh and X-forwarding, install openssh-server on the remote system, then open a terminal and type:

```
ssh -X user@server
```

once logged on to the remote system, type the name of the program you want to run, eg:

```
nautilus
```

to run the file manager.

For a howto on setting up openssh-server have a look[ here]("http://https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html"). To setup private/public key log on check out [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") howto

---

### Post by ivolution on 2010-12-27
thanks again!

Actually.. I need the real deal because it's connected as mediacenter to my tv also.. I want to be able to browse and start music and / or movies. once running I quit the connection. 

Maybe... I'm asking to much..

---

### Post by ivolution on 2010-12-28
I have installed xrdp, it works but still not at the login gdm..
Maybe I need to make xrdp be started at reboot? How?

---

