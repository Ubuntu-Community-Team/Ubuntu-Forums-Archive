---
title: "SSH connection refused from Mac, but works from Ubuntu"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by cybertoast on 2009-11-25
I've got a pristine 9.04 server with sshd running. ssh'ing to this server from my Macbook Pro gives me:
```

$ ssh foo@172.24.1.67
write: Broken pipe

```
then retrying I get:
```

$ ssh foo@172.24.1.67
ssh: connect to host 172.24.1.67 port 22: Connection refused

```

If I then connect to the server from my Ubuntu 9.04 desktop (or 9.10 desktop) box I get:
```

$ ssh foo@172.24.1.67
foo@172.24.1.67's password: 

```

If I then go back to my mac and try the connection again, I get the password prompt, and I can log in if I proceed.

If I leave everything sitting for a while the server goes back into the state where the Mac client is refused connection.

The problem does not ever happen with my 9.04 desktop box. This is a standard install of 9.04 server, and openssh-server was installed using apt-get.

The Mac has no problems connecting to the 9.04 desktop machine.

Any ideas on what could possibly be causing this weirdness?

---

### Post by puppywhacker on 2009-11-25
run the ssh client in verbose mode to give some deeper insight in where in the process it fails.

```
ssh -v foo@172.24.1.67

```

---

### Post by cybertoast on 2009-11-30
Enabling verbose mode gives me:
```

$ ssh -v foo@172.24.1.67
OpenSSH_5.3p1, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /opt/local/etc/ssh/ssh_config
debug1: Connecting to 172.24.1.67 [172.24.1.67] port 22.
debug1: Connection established.
debug1: identity file /Users/cybertoast/.ssh/identity type -1
debug1: identity file /Users/cybertoast/.ssh/id_rsa type 1
debug1: identity file /Users/cybertoast/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
write: Broken pipe

```

The solution seems to be to completely uninstall openssh-server and everything associated with it (ssh, openssh-client, etc.), then reinstall. I found this to work:
```

sudo apt-get install openssh-server openssh-client openssh-blacklist openssh-blacklist-extra keychain

```

It's a bit of a shotgun approach and guesswork, but some package obviously got corrupted and now things are working fine. Of course it's possible that the problem is not resolved since I had intermittent issues with this, so I'll report back in a day or so with more details, and if this actually *did* solve my problem :)

---

### Post by puppywhacker on 2009-11-30
I guess a full disk could generate such an event, or a file which is not "happy" so than reinstalling the packages may help. With happy I mean for instance a logfile that can not be written or a config file that could not be read.

the verbose did not really give that much feedback as I hoped, but it shows in which phase it fails (really early)

You could run "sudo strace ssh -v foo@172.24.1.67" for printing all debugging info, and look for something like "ERR". They can be a bit hard to read though.

---

