---
title: "Unable to ssh to my server from behind draconian school firewall"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by yanom on 2012-09-06
I'm trying to SSH to my home server from school. We have a pretty draconian filter/firewall here (whitelist based. seriously.), but I've assured that my IP is on the whitelist, and I can in fact visit my IP with a web browser and see the web server I've set up on the machine. But when I try SSH'ing in with PUTTY or similar, I get:
```

ubuntu@ubuntu:~$ ssh 70.239.162.206
Connection closed by 70.239.162.206

```

indicating that it's infact my server machine that doesn't want to accept connections from me from behind the firewal. How do I fix this?
oh, and ssh -vvv give this:
```

ubuntu@ubuntu:~$ ssh -vvv 70.239.162.206
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 70.239.162.206 [70.239.162.206] port 22.
debug1: Connection established.
debug1: identity file /home/ubuntu/.ssh/id_rsa type -1
debug1: identity file /home/ubuntu/.ssh/id_rsa-cert type -1
debug1: identity file /home/ubuntu/.ssh/id_dsa type -1
debug1: identity file /home/ubuntu/.ssh/id_dsa-cert type -1
debug1: identity file /home/ubuntu/.ssh/id_ecdsa type -1
debug1: identity file /home/ubuntu/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Connection closed by 70.239.162.206

```

---

### Post by SlugSlug on 2012-09-06
is port 22 blocked by the firewall

and you probably should hash out your IP

---

### Post by yanom on 2012-09-07
> **SlugSlug said:**
> is port 22 blocked by the firewall
I'm able to SSH to other places, such as GitHub (they don't provide shell access, but git'ing is done over the SSH protocol, and you can log in via SSH to confirm the connection works. It does.

> and you probably should hash out your IP
what do you mean by this? It's the school's internet hookup I'm using try and SSH, not a personal connection.

---

### Post by SlugSlug on 2012-09-07
the IP in the code boxes


  is ssh server installed on your home box?

---

### Post by yanom on 2012-09-07
> **SlugSlug said:**
> the IP in the code boxes


  is ssh server installed on your home box?

yes, on the server (also in my house) that I'm trying to connect to and on my PC

---

### Post by iponeverything on 2012-09-07
you can set a root cron to start sshd in debug mode every 5 minutes if it is not running and have its stdout and stderr redirected to file - in debug it accept 1 connection then exit.

connect a couple of times from from school - when you get home check your debug file.

---

### Post by yanom on 2012-09-10
here's an interesting insight:

1) I tried to SSH in from school, got the "connection closed by 70.239.162.206" again.

2) Came back home, SSH'ed in from my home computer. The welcome message on server login said:

```
Last login: Sun Sep  9 13:42:50 2012 from 70-239-162-206.lightspeed.snantx.sbcglobal.net

```

Several things:

1) 70.239.162.206 is my home internet IP and thus the IP of the server
2) "lightspeed" is the name of the internet filtering/firewall service my school uses
3) that "last login" time is indeed the time I tried to log in at.

---

### Post by opensshd on 2012-09-10
[http://daniel.haxx.se/docs/sshproxy.html](http://daniel.haxx.se/docs/sshproxy.html)

?

---

