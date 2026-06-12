---
title: "How do I VNC via SSH when both are not set to use the default port numbers?"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-07-07
Let's say....

I have a server.  It has SSH setup on it, but it's not using port 22.  Pretend it's port 4444.

I also have VNC configured on this server to accept incoming connections, but instead of listening on port 5900, it's listening on 5901.

Now I've used this following base command before:

```
vncviewer -via user@host localhost:0
```

But since I'm not using non default ports, I'm not sure how to alter this command to compensate for this.  I tried something like this:

```
vncviewer -via user@host:4444 localhost:1
```

As well as replacing the 1 with 5901 after the localhost: part but that results in the same message (changed the hostname of course):

> VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ssh: Could not resolve hostname host:4444: Name or service not known

Tue Jul  7 23:48:03 2009
 main:        unable to connect to host: Connection refused (111)


Both services are being port forwarded to the computer right now and both work separately; I can SSH and VNC into the same computer, but can't figure out how to VNC via SSH when it's listening on non-standard ports...

What am I doing wrong?

---

### Post by diablo75 on 2009-07-08
Bump.

Any just to clarify, I did not use the actual hostnames/addresses in the above commands.  They only serve as an example, so all I'm interested in learning about is how I need to adjust the syntax.

---

### Post by Brandon Williams on 2009-07-08
I can see two possibilities.

1) specify the port number in your ~/.ssh/config so that it doesn't need to be specified as part of the via option
```
Host host
Port 4444
```

2) use the VNC_VIA_CMD environment variable to add a -p switch to the ssh commandline

---

### Post by diablo75 on 2009-07-08
> **Brandon Williams said:**
> I can see two possibilities.

1) specify the port number in your ~/.ssh/config so that it doesn't need to be specified as part of the via option
```
Host host
Port 4444
```

2) use the VNC_VIA_CMD environment variable to add a -p switch to the ssh commandline

Could you (or maybe someone else) explain a little more on either of these options?  I do not have a file or folder called ~/.ssh/config, only an id_rsa file and a known_hosts file.  I do however have a /etc/ssh/ssh_config file that can be edited, but I was under the impression that the contents of this file pertained only to ssh-server, and not the client.  I could be wrong...

I also have no idea how to set the VNC_VIA_CMD variable.

---

### Post by Brandon Williams on 2009-07-08
Create the ~/.ssh/config file if it doesn't exist. Be careful with the permissions. The file must be writeable by you and you only. The content that I suggested will tell ssh to always use port 4444 when you connect to the hostname 'host'.

Look at the man page for vncviewer in the section about the -via flag to get more information about the VNC_VIA_CMD variable. I haven't use the variable myself. I think you would do something like this:

```
VNC_VIA_CMD='/usr/bin/ssh -p 4444 -f -L "$L":"$H":"$R" "$G" sleep 20' vncviewer -via user@host localhost:1
```

Putting the VNC_VIA_CMD assignment on the command line will set the variable in the environment for the vncviewer command.

---

