---
title: "Connection Timeout to SSH Server"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by derelict888 on 2009-07-17
I've had a file server running at home for a few months and I've used SSH to work on it while at work. Recently I cannot connect to the server, any attempts timeout. Here is an example;
```
[user]@[local-user]:~$ ssh -v root@[server]
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to [server] [#.#.#.#] port 22.
debug1: Connection established.
debug1: identity file /home/[user]/.ssh/identity type -1
debug1: identity file /home/[user]/.ssh/id_rsa type 1
debug1: identity file /home/[user]/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
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
debug1: Invalid hashed host line 1 of /home/[user]/.ssh/known_hosts
debug1: Invalid hashed host line 1 of /home/[user]/.ssh/known_hosts
debug1: Host '[server]' is known and matches the RSA host key.
debug1: Found key in /home/[user]/.ssh/known_hosts:95
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/[user]/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/[user]/.ssh/identity
debug1: Trying private key: /home/[user]/.ssh/id_dsa
debug1: Next authentication method: password
root@[server]'s password:

(... timeout for around 2-3 minutes... )
 
Connection closed by #.#.#.#
```
Any ideas? I've tried connecting from different machines all with the same result (but I can still SSH into other servers). Thing I don't understand is this has never been a problem until recently, and I don't remember changing any system settings. Any ideas? Thanks for any help.

-John

---

