---
title: "passwordless ssh"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by twowheeler on 2010-06-12
I am trying to set up a public/private key SSH with no passwords, with my lucid laptop as the client and a FreeNAS box as the server.  I generated a new key and transferred the public key to the server.  This is the verbose output:

```

dan@danslaptop:~$ ssh -v -p 4285 dhassell@fakeurl.org
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to fakeurl.org [100.100.100.100] port 4285.
debug1: Connection established.
debug1: identity file /home/dan/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2p1-hpn13v6 FreeBSD-openssh-portable-overwrite-base-5.2.p1_2,1
debug1: match: OpenSSH_5.2p1-hpn13v6 FreeBSD-openssh-portable-overwrite-base-5.2.p1_2,1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[fakeurl.org]:4285' is known and matches the DSA host key.
debug1: Found key in /home/dan/.ssh/known_hosts:15
debug1: ssh_dss_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/dan/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

```

I don't understand why this fails.  Can anybody make a suggestion?

(FYI, the URL and IP address in this output has been changed.)

Edit: here is the server /etc/ssh/sshd_config

```

SyslogFacility LOCAL3
Protocol 2
UseDNS no
Subsystem       sftp    /usr/libexec/sftp-server
ChallengeResponseAuthentication no
Port 22
AllowTcpForwarding no
Compression yes
PasswordAuthentication no
PubkeyAuthentication yes

```

And here is the client's /etc/ssh/ssh_config, omitting the comments.

```

    IdentityFile ~/.ssh/id_dsa
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

---

### Post by twowheeler on 2010-06-14
bumpety bump

---

### Post by twowheeler on 2010-06-17
Ok, found the answer.  The logs contained a lot of this:

> 
Authentication refused: bad ownership or modes for directory /mnt


and some googling revealed that ssh is very picky about the permissions on the directory you are trying to connect to.  In fact, it insists that you lock down the parent directory with mode 700.  Once that was done it worked.
Carry on.

---

### Post by Iowan on 2010-06-17
I should probably subscribe or bookmark the thread - I'm sure I'll be looking for the information later. 
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

