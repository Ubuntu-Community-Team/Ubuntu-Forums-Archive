---
title: "ssh connection dies!"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by joschum on 2010-03-02
Hi,

I have a problem initiating an ssh-connection. I was able to connect to a server for two years now without any problems but today I experienced the following error:

```
bee@laptop:~$ ssh -v serverURL
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/bee/.ssh/config
debug1: Applying options for serverURL
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to serverURL [IP-Address] port 22.
debug1: Connection established.
debug1: identity file /home/bee/.ssh/identity type -1
debug1: identity file /home/bee/.ssh/id_rsa type -1
debug1: identity file /home/bee/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'serverURL' is known and matches the RSA host key.
debug1: Found key in /home/bee/.ssh/known_hosts:11
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Connection closed by server-IP
```

I would be thankful for any help since I can`t work without solving this problem! :roll:

---

### Post by joschum on 2010-03-02
I checked that the problem does not depend on the user settings by creating a new user account, generating a new public/private key pair, importing the public key to the server, and trying to connect to the server. Same problem, connection dies, although a colleague of mine successfully just logged in to the server.

---

