---
title: "NX problem ssh connection timed out"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by Dan Z on 2012-09-27
Been using NX for quite a while, now a problem. When I try to log on to my Ubuntu 10.04 I get this error:

ssh:connect to host xxxxxxxxxx port 22: connection timed out



checking my notes, they say ssh must be running, but it does not seem to be. I cannot find it running under System monitor or when I run ps aux. 

If I run $ start ssh
start: Job is already running: ssh

I recall this happened another time and I had to restart ssh, but can't figure out how.

thanks Dan

---

### Post by Dan Z on 2012-09-27
> **Dan Z said:**
> Been using NX for quite a while, now a problem. When I try to log on to my Ubuntu 10.04 I get this error:

ssh:connect to host xxxxxxxxxx port 22: connection timed out



checking my notes, they say ssh must be running, but it does not seem to be. I cannot find it running under System monitor or when I run ps aux. 

If I run $ start ssh
start: Job is already running: ssh

I recall this happened another time and I had to restart ssh, but can't figure out how.

thanks Dan
problem solved--- IP of server PC somehow changed, caused port forward to fail. changed IP in port forward ok now

---

