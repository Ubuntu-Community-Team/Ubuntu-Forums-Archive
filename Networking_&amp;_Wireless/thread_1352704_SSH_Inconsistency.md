---
title: "SSH Inconsistency"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by wgcampbell on 2009-12-11
Both machines running XUbuntu 9.10 and OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007

I'm trying to run a reverse SSH tunnel.  I'm using the following command line:

```
ssh -f -N -R 4411:localhost:22 geoff@sshserver.dnsalias.com
```

On the sshserver, I get the following error:
 
```
Dec 11 10:27:46 sshserver sshd[3713]: pam_unix(sshd:session): session opened for user geoff by (uid=0)
Dec 11 10:27:47 sshserver sshd[3778]: error: bind: Address already in use
```

Most of the time, this doesn't hurt anything - the connection is still made and the port (4411) is still usable.

But sometimes, I in addition to the above, I get this additional error:

```
Dec 11 10:27:48 sshserver sshd[3778]: error: channel_setup_fwd_listener: cannot listen to port: 4411
```

This is then a problem as I cannot connect over port 4411.

There seems to be not much consistency, however I always get the "Address already in use" error, no matter what port (or ports) that I use.

Additionally, this happens only on one machine (both machines are the same version of XUbuntu and the same version of OpenSSH (see above).

If I turn the machines around and tunnel the sshserver machine back to the remote machine, I don't get the error.

Also, I have tried copying the ssh and sshd config files from the remote machine (which works) to the sshserver machine.  This doesn't solve the problem

I have tried substituting the actual IP address or 127.0.0.1 for localhost, doesn't help.  I have found other posts concerning "bind: Address already in use" - tried all of those solutions, but nothing seems to work.

Can anybody help?

---

### Post by iponeverything on 2009-12-12
Digging around abit a google, it appears that ssh will not reuse a port if it is in a TIME_WAIT state if "X11UseLocalhost=no" is set in the sshd.conf file.

Changing X11UseLocalhost=no to X11UseLocalhost=yes should change this behaviour and might solve your problem.

---

### Post by wgcampbell on 2009-12-12
I had seen that but figured since my ssh and sshd config files were exactly alike, that wouldn't be a factor.  But anyway, I tried it and it made no difference.

Just to clarify, it happens every time I try to reverse ssh to this machine (the sshserver) - even first time after a reboot.  So I figure the wait state would make no difference.

But thanks for the suggestion - I'm willing to try anything - any other suggestions?

---

### Post by wgcampbell on 2009-12-12
More Info:

It seems that although my ssh_config and sshd_config files were the same, I forgot to restart the sshd server.  Anyway it turns out that the "GatewayPorts" option in the sshd_config file (on the server) is the problem.  

So I guess my question has become, how do you setup a reverse ssh tunnel with "GatewayPorts" set to either "yes" or "clientspecified", without getting the "bind: Address already in use" error?

---

### Post by wgcampbell on 2009-12-13
Solution (sort of)

It seems that the entire problem is caused by setting the (sshd) option GatewayPorts to either yes or clientspecified.

Also, if you have set the GatewayPorts option (as above) then your reverse ssh tunnel (seemingly) must have 4 parameters. (If you don't specify 4 parameters, you'll get the "bind: address already in use" error every time.)  And the first parameter (the bind address) must be the IP address of the "server" interface.

Still getting the "bind: address already in use" errors every once in a while - so the problem is not totally solved.

Hope that helps somebody.:D

---

