---
title: "ssh :read from socket failed :connection reset by peer"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by Satya on 2012-02-05
I am unable to ssh properly ...even though connection is getting established it is reset by peer after "SSH2_MSG_KEXINIT sent"

kindly help
 ssh -v -p 31000 localhost
gives


OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 31000.
debug1: Connection established.
debug1: identity file /home/hduser/.ssh/identity type -1
debug1: identity file /home/hduser/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/hduser/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

---

### Post by dmizer on 2012-02-06
Do you have anything in /var/log/auth.log regarding ssh?

---

