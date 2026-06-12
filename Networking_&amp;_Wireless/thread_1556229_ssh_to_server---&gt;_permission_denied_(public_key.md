---
title: "ssh to server---&gt; permission denied (public key)"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by wannabegeek on 2010-08-19
hi all

I'm working on my media server and trying to set up ssh to work through DynDNS.com, 
only using keys. I think I have it working with password from outside but not sure.
Starting from home, is not working.

first issue: from home, where both machine are behind the router, I can't ssh to the server:
```
ssh -v remote@10.0.0.10
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.0.0.10 [10.0.0.10] port 22.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug1: identity file /home/daniel/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/daniel/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
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
debug1: Host '10.0.0.10' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/daniel/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/daniel/.ssh/identity
debug1: Trying private key: /home/daniel/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```

I changed the sshd_config on the server to no passwords...it's a drag not being able to cut and paste...so a little lazy here reporting all details...

Copied my pub key from laptop to server with USB drive and placed in
~/.ssh/authorized_keys

permissions for .ssh are 700 and tried 400 for authorized_keys...

still no luck....:confused:

tia
wbg

---

### Post by surfer on 2010-08-19
did you read and follow [this thread]("http://ubuntuforums.org/showthread.php?t=30709")?

---

### Post by wannabegeek on 2010-08-19
pretty close...used rsa ket instead....tried again using the thread posted and made dsa key...
I suppose I need to change sshd_config for dsa keys ?

EDIT: found authentication of keys line on sshd_config...I uncommented the line and changed the %h to actual path...
I'm the only one who logs into this server...restarted shh with ```
/etc/init.d/ssh restart
``` no errors but also 
not working yet

---

### Post by wannabegeek on 2010-08-19
bump....

---

