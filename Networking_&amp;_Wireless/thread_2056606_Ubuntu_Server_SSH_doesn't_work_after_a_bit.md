---
title: "Ubuntu Server SSH doesn't work after a bit"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by pengyou on 2012-09-11
I set up an SSH server on a computer connected by ethernet cord to the router, then used
```

ssh-keygen -t rsa

```to generate an RSA key on my laptop, connected wirelessly to the router.
My sshd is configured like so:
```

cat /etc/ssh/sshd_config 
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 6574
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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
#PasswordAuthentication yes

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

```I then moved the public key to the server, and **all works fine after a reboot of the system**, but **after awhile **things go awry, and **nothing will help but another reboot.**
Using
```

ssh -p 6574 username@10.0.0.5 -v

```gets me things like: "agent admitted failure to sign using the key".
I would gladly post the full output of this, but I will need to wait until the problem reoccurs, having just restarted.
I will need to leave for class in 24 or so minutes, and will be back a few hours after that, at which point I expect the problem will reoccur.

My /var/log/auth.log has lines like:
```

Sep 11 16:13:38 SERVER sshd[6391]: Server listening on 0.0.0.0 port 6574.
Sep 11 16:13:38 SERVER sshd[6391]: Server listening on :: port 6574.
Sep 11 16:13:49 SERVER sshd[6392]: Connection closed by 10.0.0.99 [preauth]

```The last of which appears every time my attempt to login fails.

EDIT:
Running Ubuntu server, if that helps at all

---

### Post by pengyou on 2012-09-11
Just exited my session and attempted to SSH again, this time I get:
```

debug1: found matching key w/out port
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/username/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Offering RSA public key: /home/username/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/username/.ssh/id_ecdsa
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```
at the end...
I'm not prompted for a passphrase either...

---

### Post by pengyou on 2012-09-11
It seems that now I have to be logged in on the server (as in, using the keyboard and mouse attached to it) in order to SSH into it over LAN.
Is there a way to get around this? How can I start listening for SSH and get in without having to enter my username and password?
I'm no longer getting any acknowledgement of failure to sign.

---

### Post by papibe on 2012-09-12
Hi pengyou.

By any chance your /home partition is encrypted?

If so, you need a special configuration in order for the ssh keys to work.

Regards.

---

