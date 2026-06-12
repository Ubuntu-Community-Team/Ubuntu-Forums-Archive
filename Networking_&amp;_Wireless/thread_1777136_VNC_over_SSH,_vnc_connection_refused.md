---
title: "VNC over SSH, vnc connection refused"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by Gluebuntu on 2011-06-07
I want to create a vnc connection to a remote server through an ssh tunnel, I'm using keys to do this so there is no password stuff.

I try to go:

```

ssh -v -C -p 21 -L 5901:127.0.0.1:5900 <username>@<remote ip>

```

But after I ssh into the server, and try to connect to 127.0.0.1::5901 with Remote Desktop Viewer on my local machine, I get:

```

debug1: Local forwarding listening on 127.0.0.1 port 5901.
debug1: channel 0: new [port listener]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Connection to port 5901 forwarding to 127.0.0.1 port 5900 requested.
debug1: channel 1: new [direct-tcpip]
channel 1: open failed: connect failed: Connection refused

```

On the remote server.

And Remote Desktop Veiwer creates a pop-up window that says:

```

Connection to 127.0.0.1::5901 closed

```

I have googled around and many other people have had this problem, but I can't figure it out. I have the firewall setup and sshd configured.

Here is significant part of the ufw on the remote machine:

```

5900                       ALLOW       127.0.0.1
21                         ALLOW       Anywhere

```

The weird thing is that this used to be working but stopped for some reason.

I thought this problem might be a bit beyond absolute beginner, so I posted it in here, but I'm still new to Linux so please explain things in detail to me, thanks.

If there is any thing I can do to give more detail please just tell me.

---

### Post by gmargo on 2011-06-07
This is your main clue:
> **Gluebuntu said:**
> ```

channel 1: open failed: connect failed: Connection refused

```

Why was the connection refused?  Is any process listening on port 5900 on the server?  Does that process have a log file that might give more info?

---

### Post by Gluebuntu on 2011-06-07
Well, I used the ubuntu GUI on my server machine and set it so that any one (within the firewall) can connect to my machine with vnc, so I don't understand why that would fail. :sad:

I setup the server the same way they did in the first part of _[this]("http://blog.sudobits.com/2011/03/13/vnc-server-for-ubuntu-10-10/")_ tutorial. So I would be using Vino, is there a way I can see the logs for that? :confused:

---

### Post by Gluebuntu on 2011-06-07
Wow, that's so weird! I just tried connecting again, and it worked! The remote desktop computer was able to connect! Hmmm.... I'll post back in a bit when I have an idea why that happened.

---

### Post by Gluebuntu on 2011-06-07
Well, I think the problem was the the VNC server wasn't running, which is weird because while I was having the problem, I went (physically) to my server and it was just on the login screen, which shouldn't be a problem since the VNC server runs at system startup.

Do I have to be graphically logged in to connect to  the VNC server or is this a one-off? :-?

---

