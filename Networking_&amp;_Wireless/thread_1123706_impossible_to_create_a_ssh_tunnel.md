---
title: "impossible to create a ssh tunnel"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by debuntu7561 on 2009-04-12
Hi,

I can't create a ssh tunnel between my pc and a domain.

here is the error message I have:

Any idea of the problem?

```

OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/jef/.ssh/config

debug1: Reading configuration data /etc/ssh/ssh_config

debug1: Applying options for *

debug1: Connecting to vtt####.org [##.##.###.###] port 22.

debug1: Connection established.

debug1: identity file /home/jef/.ssh/identity type -1

debug1: identity file /home/jef/.ssh/id_rsa type -1

debug1: identity file /home/jef/.ssh/id_dsa type 2

debug1: Remote protocol version 1.99, remote software version OpenSSH_3.9p1

debug1: match: OpenSSH_3.9p1 pat OpenSSH_3.*

debug1: Enabling compatibility mode for protocol 2.0

debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2

debug1: SSH2_MSG_KEXINIT sent

debug1: SSH2_MSG_KEXINIT received

debug1: kex: server->client aes128-cbc hmac-md5 none

debug1: kex: client->server aes128-cbc hmac-md5 none

debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP

debug1: SSH2_MSG_KEX_DH_GEX_INIT sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY

debug1: read_passphrase: can't open /dev/tty: No such device or address
debug1: permanently_drop_suid: 1000
ssh_askpass: exec(/usr/bin/ssh-askpass): No such file or directory
Host key verification failed.

```

thanks

JEef

---

### Post by dmizer on 2009-04-13
Looks like the server isn't listening on the remote port. On the remote router, are you sure that [port 22 is forwarded](http://portforward.com/) to the listening ssh server?

---

