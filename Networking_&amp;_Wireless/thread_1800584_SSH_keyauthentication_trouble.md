---
title: "SSH keyauthentication trouble"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by mzycdth on 2011-07-09
Hi everyone,

I'm trying to set up my ssh keyauthentication again after purging but keep getting a permission denied (publickey) error once I turn off password authentication.


debug1: sshd version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Bind to port 22 on 0.0.0.0 failed: Address already in use.
Cannot bind any address.
user@local:~$ ssh -v user@IP
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to IP [IP] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/plyzct/.ssh/id_rsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu5
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1 expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1 Server host key: RSA 76:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
debug1 Host 'IP' is known and matches the RSA host key.
debug1 Found key in /home/user/.ssh/known_hosts:1
debug1 ssh_rsa_verify: signature correct
debug1 SSH2_MSG_NEWKEYS sent
debug1 expecting SSH2_MSG_NEWKEYS
debug1 SSH2_MSG_NEWKEYS received
debug1 Roaming not allowed by server
debug1 SSH2_MSG_SERVICE_REQUEST sent
debug1 SSH2_MSG_SERVICE_ACCEPT received
debug1 Authentications that can continue: publickey
debug1 Next authentication method: publickey
debug1 Offering RSA public key: /home/user/.ssh/id_rsa
debug1 Authentications that can continue: publickey
debug1 No more authentication methods to try.
Permission denied (publickey).

I've checked both the local and remote keys stored in id_rsa.pub and they match.

I've also moved id_rsa.pub on the remote machine from user/.ssh/authorized_keys to /etc/ssh/user/authorized_keys and changed the link in the /etc/ssh/sshd_config to indicate this.

---

