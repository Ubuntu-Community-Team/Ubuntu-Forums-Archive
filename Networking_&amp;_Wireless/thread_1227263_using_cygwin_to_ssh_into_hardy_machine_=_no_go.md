---
title: "using cygwin to ssh into hardy machine = no go?"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by aaronLund on 2009-07-30
Trying to ssh into my Hardy computer from my wife's Windows (xp) laptop using Cygwin.

Doesn't wanna do it. 

Here's the verbose output from my ssh attempt:

Any clues?

What's weird is that I don't have a folder/file called "identity" on the windows box.  

Thanks.

```

Administrator@rhubarb ~
$ ssh -v 192.168.0.2
OpenSSH_5.1p1, OpenSSL 0.9.8h 28 May 2008
debug1: Connecting to 192.168.0.2 [192.168.0.2] port 22.
debug1: Connection established.
debug1: identity file /home/Administrator/.ssh/identity type -1
debug1: identity file /home/Administrator/.ssh/id_rsa type -1
debug1: identity file /home/Administrator/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debia
n-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /home/Administrator/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/Administrator/.ssh/identity
debug1: Trying private key: /home/Administrator/.ssh/id_rsa
debug1: Offering public key: /home/Administrator/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

Administrator@rhubarb ~
$
```

---

### Post by aaronLund on 2009-07-30
Solved.

I needed to give the username of the host in the ssh command.

So instead of

```
ssh ipaddress.of.host
```

I needed to do 

```
ssh myname@ipaddress.of.host
```

I love it when a plan comes together.

---

