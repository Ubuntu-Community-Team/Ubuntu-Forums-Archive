---
title: "FreeNX Busted Authentication"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by Quantumstate on 2009-01-02
Well, maybe this is not going to work out with freenx.  I installed the Ubuntu packages from here into Intrepid:
ppa.launchpad.net/freenx-team/ubuntu

First of all, it is insisting on logging into SSH as user nx.  This forced me to add nx to SSH AddUsers, which I'd rather not have done.  Then it got alot further in login, accepting the (custom) public key, but then it fails on my username login for some reason.  So maybe I need to add my username to nx, as I did with VNC:
```
# nxserver --adduser bill
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 500 Error: The passdb function is not activated in node.conf.

Most probably your FreeNX setup will work out of the box without this
functionality and you've been misleaded by an old tutorial or old
documentation to do this step.

If however you really need this functionality, just set
ENABLE_PASSDB_AUTHENTICATION="1" in node.conf.

NX> 999 Bye
```

Unfortunately though, it does *not* work out of the box, and I wasn't 'misleaded' by anything since I installed from the Ubuntu repository.  Why would it need to log in not only as nx, but also as me?  Yet it says this mode is outdated?  This seems busted.  So OK I gave in and enabled the passwd database for nx:

```
(set ENABLE_PASSDB_AUTHENTICATION="1", restart freenx server)

# nxserver --adduser bill
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
Running /etc/profile
grep: /etc/ssh/sshd_config: Permission denied
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
cat: /etc/nxserver/users.id_dsa.pub: No such file or directory
cat: /etc/nxserver/users.id_dsa.pub: No such file or directory
NX> 716 Public key added to: /home/bill/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye
cygnus:/etc/init.d # nxserver --passwd bill
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
New password:
Password changed.
NX> 999 Bye

Jan  2 11:58:04 hex su[13093]: pam_unix(su:session): session opened for user bill by (uid=0)
Jan  2 11:58:04 hex su[13093]: pam_unix(su:session): session closed for user bill
Jan  2 11:59:37 hex sshd[13309]: Accepted publickey for nx from 192.168.1.1 port 45945 ssh2
Jan  2 11:59:37 hex sshd[13309]: pam_unix(sshd:session): session opened for user nx by (uid=0)
Jan  2 11:59:39 hex sshd[13501]: Accepted password for bill from 127.0.0.1 port 49090 ssh2
Jan  2 11:59:39 hex sshd[13501]: pam_unix(sshd:session): session opened for user bill by (uid=0)
Jan  2 11:59:40 hex sshd[13501]: pam_unix(sshd:session): session closed for user bill
Jan  2 11:59:43 hex nxserver[13593]: (nx) Failed login for user=bill from IP=192.168.1.1
Jan  2 11:59:43 hex sshd[13309]: pam_unix(sshd:session): session closed for user nx
```
OK, so it's accepting authentication now for nx and for me, but it's still dumping out the session for reasons which are mysterious.

I thought OK, I didn't RTFM.  Unfortunately though, I then found that the manual basically says it should 'just work', and the 'Quick Start' guide is just a list of node.conf settings, not a guide.

As there is absolutely no explanation of the mechanics of this thing, I have no way of tracing the chain to failure.  Doesn't anyone have any sense these days?

Ideally I would like to not involve the nx user in any way, have it use my credentials to log in through SSH, and set the session up SSH encrypted (not SSL).  Looks impossible though.

---

### Post by dasbooter on 2009-03-04
oh well I am also using the newest ppa launch pad packages which I think were just updated not too long ago ... and now I am also getting authentication failure on a previous working installation. As to the user who started the thread I am not sure but I thought that the user nx thing is by design and I know for sure that I did not have to add the user nx to access ssh. Sounds like something went funky with your install. Anyways I can login via ssh but freenx remains broken anybody else care too add there 2 cents into this old thread.

---

