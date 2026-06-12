---
title: "SSH Public Key Denied"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by jasneet on 2010-11-18
I set up an SSH server on my home machine and finally figured out that I needed to disable password authentication to get RSA authentication enabled. Now I'm having problems with that too.

**ssh -v -i id_rsa.pub ashtray@x.x.x.83**

```

OpenSSH_5.1p1 Debian-5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 68.100.5.83 [68.100.5.83] port 22.
debug1: Connection established.
debug1: identity file id_rsa.pub type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '68.100.5.83' is known and matches the RSA host key.
debug1: Found key in /home/a/ashtray/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: id_rsa.pub
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

```

Its weird because it says "signature correct" So if it can verify it's the correct signature what could the problem be?

sshd_config

```

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```

Unsure about where the keys belonged, I put the keys in the /user/.ssh folder and in /user/.ssh/authorized_keys

File permissions folder /user/.ssh
-rw-r--r-- 1 ashtray ashtray 213 2010-11-14 05:58 ssh

Inside the folder:

drw-r--r-- 2 ashtray ashtray 4096 2010-11-17 05:11 **authorized_keys**
-rw------- 1 ashtray ashtray 1675 2010-11-17 02:32 id_rsa
-rw-r--r-- 1 ashtray ashtray 405 2010-11-17 02:32 id_rsa.pub
-rw-r--r-- 1 ashtray ashtray 2210 2010-11-17 04:58 known_hosts
-rw------- 1 ashtray ashtray 1675 2010-11-17 04:44 ssh.shellium.org (I ssh from shellium but have no idea how this got here)

Inside of **authorized_keys** folder:

```

-rw-r--r-- 1 ashtray ashtray 1675 2010-11-17 02:32 id_rsa
-rw-r--r-- 1 ashtray ashtray  405 2010-11-17 02:32 id_rsa.pub

```

The keys on the client on I'm using to access the server:

```

-rw-r--r--  1 ashtray users 1675 2010-11-17 05:02 id_rsa
-rw-r--r--  1 ashtray users  405 2010-11-17 05:02 id_rsa.pub

```

Help if you can please because i've been pecking away at this for hours.

---

### Post by Ashtray2 on 2010-11-18
Thank you jasneet for posting this thread on my behalf (I created 2 threads but neither showed up in the forum).

I should add that I did a chmod 700 on .ssh folder.  chmod 600 on .ssh/authorized_keys.  and chmod 400 on the public key.  That didn't work either.  

Also realized the key that goes on the client is id_rsa not id_rsa.pub

---

