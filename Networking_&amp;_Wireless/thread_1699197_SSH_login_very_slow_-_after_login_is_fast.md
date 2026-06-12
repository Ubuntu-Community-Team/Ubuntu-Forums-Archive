---
title: "SSH login very slow - after login is fast"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by josir on 2011-03-03
Hi folks, on a particular Ubuntu 8.04 server, ssh is very slow at login. Digging around, I comment the following parameters on ssh_config.conf

#SSAPIAuthentication yes
#GSSAPIDelegateCredentials no

But it didn't work either. Here is a debug session:

supervisor@linux02:/srv$ ssh -C -v fabricio@192.168.0.6
OpenSSH_5.3p1 Debian-3ubuntu5, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.6 [192.168.0.6] port 22.
debug1: Connection established.
debug1: identity file /home/supervisor/.ssh/identity type -1
debug1: identity file /home/supervisor/.ssh/id_rsa type -1
debug1: identity file /home/supervisor/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 [email]zlib@openssh.com[/email]
debug1: kex: client->server aes128-ctr hmac-md5 [email]zlib@openssh.com[/email]
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.6' is known and matches the RSA host key.
debug1: Found key in /home/supervisor/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received

--- Here it takes almost one minute...

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/supervisor/.ssh/identity
debug1: Trying private key: /home/supervisor/.ssh/id_rsa
debug1: Trying private key: /home/supervisor/.ssh/id_dsa
debug1: Next authentication method: password

Does anybody have any glue?

Thanks in advance,
Josir Gomes

---

### Post by ph8 on 2011-12-21
Did you ever fix this problem Josir?

---

### Post by josir on 2011-12-21
Yes!

Just add the parameter "UseDNS no" on 

/etc/ssh/sshd_config

Good Luck.
Josir

---

### Post by CharlesA on 2011-12-21
Guess it was doing a reverse DNS lookup.

```
     UseDNS  Specifies whether sshd(8) should look up the remote host name and
             check that the resolved host name for the remote IP address maps
             back to the very same IP address.  The default is ``yes''.
```

In any case, here is what that option does.

---

