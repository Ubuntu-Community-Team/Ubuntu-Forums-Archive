---
title: "Can't ssh into local ubuntu server"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by LiefhebberLinux on 2012-03-01
Hi,

I have set-up a local ubuntu server (11.10) and now I would like to ssh into it. However I am getting the following message after 
"
ssh -v jack@192.168.0.120 (my server ip)

jack@LAPTOP-jack:~$ ssh -v jack@192.168.0.120
OpenSSH_5.9p1 Debian-2ubuntu2, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.0.120 [192.168.0.120] port 22.
debug1: Connection established.
debug1: identity file /home/jack/.ssh/id_rsa type -1
debug1: identity file /home/jack/.ssh/id_rsa-cert type -1
debug1: identity file /home/jack/.ssh/id_dsa type -1
debug1: identity file /home/jack/.ssh/id_dsa-cert type -1
debug1: identity file /home/jack/.ssh/id_ecdsa type -1
debug1: identity file /home/jack/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: match: OpenSSH_5.8p1 Debian-7ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-2ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA dc:1f:d6:6f:c9:f9:6e:12:cf:83:92:8c:34:66:cd:c7
debug1: Host '192.168.0.120' is known and matches the ECDSA host key.
debug1: Found key in /home/jack/.ssh/known_hosts:29
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jack/.ssh/id_rsa
debug1: Trying private key: /home/jack/.ssh/id_dsa
debug1: Trying private key: /home/jack/.ssh/id_ecdsa
debug1: Next authentication method: password
"
next I have
"
jack@192.168.0.120's password: 
Read from socket failed: Connection reset by peer
"
192.168.0.120 is my server ip (it's hostname is server, so ideally I would like to ssh into jack@server, but I don't know how to do that yet (any pointers?)). I can ping it fine. On my server I have set in my ssh config

PermitRootLogin no
AllowUsers jack

I have a Virgin Media Superhub at home where both workstation and server are located.

Cheers

---

