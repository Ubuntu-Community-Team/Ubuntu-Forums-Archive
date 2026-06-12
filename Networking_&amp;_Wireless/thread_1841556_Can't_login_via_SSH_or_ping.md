---
title: "Can't login via SSH or ping"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by Fibonacci on 2011-09-09
Hello.

Ever since I've installed Natty on a new computer (and of course an SSH server), I've been unable to login to it from outside, or ping it.
I've tried to do both from Ubuntu and from Windows, and from multiple locations, without success.
Here's what I get:
```

$ ssh -vvv myhomeserver
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to myhomeserver [###.###.###.###] port 22.
debug1: Connection established.
debug1: identity file /home/XXXXXXXXX/.ssh/id_rsa type -1
debug1: identity file /home/XXXXXXXXX/.ssh/id_rsa-cert type -1
debug1: identity file /home/XXXXXXXXX/.ssh/id_dsa type -1
debug1: identity file /home/XXXXXXXXX/.ssh/id_dsa-cert type -1
debug1: identity file /home/XXXXXXXXX/.ssh/id_ecdsa type -1
debug1: identity file /home/XXXXXXXXX/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "myhomeserver" from file "/home/XXXXXXXXX/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/XXXXXXXXX/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
$ ping myhomeserver
PING myhomeserver (###.###.###.###) 56(84) bytes of data.
^C
--- myhomeserver ping statistics ---
40 packets transmitted, 0 received, 100% packet loss, time 39290ms

```

The server, though, is online. I've installed Apache, and I can reach the default webpage from outside.
I've also tried to reach the server using telnet:
```

$ telnet myhomeserver 22
Trying ###.###.###.###...
Connected to myhomeserver.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3

Protocol mismatch.
Connection closed by foreign host.

```
Thus proving that the port is not blocked, and of course confirming that the server is online.

Finally, following suggestions found on Google, I've tried purging and reinstalling SSH, and rebooting. Needless to say, that didn't help a bit.

What else can I try?

---

### Post by Dangertux on 2011-09-09
You said purging, but did you remove your known_hosts entry from /home/$user/.ssh

Sometimes that helps.

---

### Post by Fibonacci on 2011-09-09
> **Dangertux said:**
> You said purging, but did you remove your known_hosts entry from /home/$user/.ssh

Sometimes that helps.

Just tried that. Didn't help.

Just in case I tried SSHing from a different computer. Still nothing.

---

### Post by sanderj on 2011-09-09
How about [https://wiki.archlinux.org/index.php/SSH#Read_from_socket_failed:_Connection_reset_by_peer](https://wiki.archlinux.org/index.php/SSH#Read_from_socket_failed:_Connection_reset_by_peer) ?

---

### Post by Fibonacci on 2011-09-12
> **sanderj said:**
> How about [https://wiki.archlinux.org/index.php/SSH#Read_from_socket_failed:_Connection_reset_by_peer](https://wiki.archlinux.org/index.php/SSH#Read_from_socket_failed:_Connection_reset_by_peer) ?

This did solve it – when connecting from Ubuntu.
How do I make it work with e.g. PuTTY?

---

