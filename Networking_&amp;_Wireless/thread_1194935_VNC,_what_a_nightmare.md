---
title: "VNC, what a nightmare"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by borophyll on 2009-06-23
I have been stuffing around with this **** for too long now, I've tried just about every combination of VNC server and client, and none of them work adequately.

For starters, the Remote Desktop applet is absolutely useless.  It does not start vino-server, who knows why?  Anyway, I manually start vino-server, then try to remote login from my laptop.  It connects, but I get a black screen.  Not knowing how to configure vino-server, as there is no man page or documentation on how to use the damn thing, I threw it away, and installed x11vnc.  Again it connects, and this time I do get something: extremely slow input response, mangled screen, and random disconnects.  I have tried both vncviewer and vinagre as the client.  I've tried the -noxdamage option, and it made no difference

I followed some instructions on installing vnc4server, to see if this server would make a difference. This server wouldn't even start!

I am at my wits end to get anything working.  I have spent 5 hours on something that should take at most 1/2 hour.  I have gone around in circles and am confused as to what to do next?  PLEASE HELP!

---

### Post by aurelieng on 2009-06-23
Not exactly an answer, but NX might interests you as well, since it is faster and much more secure than VNC:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by borophyll on 2009-06-23
not having much luck with it either, same problems, intermittent connection, session hangs.

---

### Post by sedawk on 2009-06-23
x11vnc is used to share an already running desktop, normally
this is DISPLAY 0.0.
This is useful (e.g. for remote administration), but a vnc connection
to another display works better.

When running a normal vnc-server you use a completely new DISPLAY
like 2.0. You have to start some window manager and some applications
on that desktop, otherwise it might be empty and not show
anything useful.

In your case there might be network problems. 
To test vnc client and server you can try to run the client on
the same computer as the vnc server and to redirect the output
of the vnc-client to the local machine (e.g. the laptop):
```

# on the laptop
ssh -X vnc_server_ip
vinagre

```
Then use vinagre to connect to your vnc-server (do not
use the IP but first "localhost". If that works try with the IP.
If that works try with a local vnc client again.)

---

