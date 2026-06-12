---
title: "Cannot connect regular user over ssh with Nautilus"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by alloydog on 2011-10-31
I am in the process of setting up a file-share server to be accessible over VPN.

The *main user* is account is the one which was created when the server was installed. It has sudo privilages.
The *regular user* accounts are normal "everyday" user accounts which cannot use sudo.

Using PuTTY from my laptop, I can log in to the server as either the *main user* or as one of the *regular user*s. When logged in as a *regular user*, commands preceeded with **sudo** are not permitted.
So far so good.

I can also log in to the server through Nautilus, as the main user, using ssh:
**ssh://*main_user*@192.168.1.100/home/*main_user***
or at any other level, even just to **/**.
The pop-up asking for the password pops-up, I enter it, hit Enter and it connects.

However, when I try to connect the same way with one of the regular user accounts, I get the password pop-up box. But when I enter the password and hit enter, it just repeats.

I also cannot connect as a regualr user to the server through **Places > Network**.
I can see the server though, and connect as the server's main user though.

I'm not sure where the problem lies, maybe with ssh?

The server is Ubuntu 10.04LTS server and my laptop is Ubuntu 10.10.

**sshd_config**
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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
```

---

### Post by alloydog on 2011-11-07
Seriuosly, no suggestions?

---

