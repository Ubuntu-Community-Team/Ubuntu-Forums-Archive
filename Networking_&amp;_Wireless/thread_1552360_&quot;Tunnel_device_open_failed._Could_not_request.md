---
title: "&quot;Tunnel device open failed. Could not request tunnel forwarding.&quot;"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by wblogan on 2010-08-13
Attempting to establish ssh tunnel with command:
	ssh -L 5910:localhost:5900 user@<ipaddress>

Login succeeds but I can't figure out "Tunnel device open failed. Could not request tunnel forwarding."

Any advice will be appreciated.

-----------------------
debug1: Authentication succeeded (password).
debug1: Local connections to LOCALHOST:5910 forwarded to remote address localhost:5900
debug1: Local forwarding listening on ::1 port 5910.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 5910.
debug1: channel 1: new [port listener]
debug1: Requesting tun unit 2147483647 in mode 1
debug1: sys_tun_open: failed to configure tunnel (mode 1): Operation not permitted
Tunnel device open failed.
Could not request tunnel forwarding.
debug1: channel 2: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
Linux <user>-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS
<user>-laptop:~$
--------------------------

---

### Post by promet on 2010-08-25
I am having this same issue. I had tried to figure this out awhile back and, sadly, couldn't resolve it. My morale is now high enough for me to try again though. I will let you know if I figure anything out. Seems like it should be simpler than this, don't it?

---

### Post by netwiz101 on 2012-03-15
I just experienced the same problem. After reading *your* logs, it occurred to me what the problem was.

You must be root to initialize the tunnel because it involves creating a device. That really means:

a) You must allow and utilize a root login on the server you are ssh-ing into.

b) (this is the one I missed): You must be logged in as root on the client initiating the tunnel -- other wise you will not have access to create the tunnel.

I'm a couple of years too late, but hopefully this is of use to someone.

---

