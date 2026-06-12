---
title: "Have Connection - Can't Use!"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by wgcampbell on 2010-02-27
I have a reverse ssh connection (using autossh) coming in to my local machine, but I can't log in.  It was working, but now is not.  I get the following:

```
ssh -p 7766 -vvv user@192.168.1.108
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.108 [192.168.1.108] port 7766.
debug1: Connection established.
debug1: identity file /home/guest/.ssh/identity type -1
debug1: identity file /home/guest/.ssh/id_rsa type -1
debug1: identity file /home/guest/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
```

I've tried everything - I can only assume that the ssh server on the remote machine is blocking connections.

But the reverse connection is there - I confirm this by killing the process on my local machine, then a new connection shows up in seconds.

So I have this established reverse connection through a specific port.  Can one of you gurus or experts out there tell me if there is another way to utilize this reverse connection other than through ssh?  Some way to get to a shell prompt on that remote server??  (It's miles away and not accessible)

---

