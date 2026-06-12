---
title: "Error 204 Authentication failed with Freenx/Nomachine"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by Cursed Lemon on 2012-11-14
I am getting the typical 204 authentication error when attempting to use  Nomachine/Freenx to connect to either local computers here in the  office or outbound ones at other sites. 

I'm attempting to use SSH authentication through a central server "hadrian". 

```

NX> 203 NXSSH running with pid: 4285
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.68 on port: 6235
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```Am I doing something  wrong here? My understanding is that Nomachine can do normal SSH  authorizations with no password needed by simply reading the  /home/USER/.ssh/authorized_keys file. 

Is there something else I need to do to make this work?

---

### Post by MidnightJava on 2012-11-16
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1490038&highlight=nxserver") for a possible solution to the authentication problem. See the post by chon near the end, with an attachment. This fixed the problem I was having with authentication after upgrading to 12.10.

However, if you're running 12.10 you're likely to run in to the problem discussed in [this thread]("http://ubuntuforums.org/showthread.php?p=12357186#post12357186") after you fix the authentication problem. No solution so far AFAIK.

---

