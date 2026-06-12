---
title: "SSH Keys Ubuntu Server, Windows Client"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by PackyIsWacky on 2013-01-18
Heeelllooooooooo everybody.

I have SSH working with putty and FileZilla with just password authentication, but I CANNOT for the life of me get SSH keys to work.  This is the deal, I have a 12.10 Ubuntu home server with an encrypted home folder.  This means that I have to put my Authorized_keys file in /etc/ssh/[my name here].

I generated the public key and private key without passwords with PuTTYgen on my windows 7 computer and named the keys:
RSAprivatekey.ppk
RSApubkey

The keys are 2048 bits.  (is that enough?)

Then, I used an USB dongle to copy the public key to the Ubuntu server.  So, in my /etc/ssh/[my name here] folder I put the RSApubkey file.  This is the ONLY file in here.  I actually don't have a file names authorized_keys.  Do I need this file?

Next, I changed the sshd_config file to this configuration:

***********************************************************
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 2222
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
ServerKeyBits 2048

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin no
AllowUsers [ny name here]
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    /etc/ssh/[my name here]/RSApubkey

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
PasswordAuthentication yes

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
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp internal-sftp

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM no

IgnoreUserKnownHosts no
PasswordAuthentication no
Match group sftponly
ChrootDirectory /home/
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp


*************************************************************

Can anyone help?  What am I doing wrong?

Thanks in advance for your help.

BTW, I have read this page and a few others like it:  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by dpurgert on 2013-01-18
you need a file named "authorized_keys" as well, detailing the keys.

pretty much do this:

```

cat RSApubkey >> authorized_keys

```

and then fix your config:
```

AuthorizedKeysFile = /etc/ssh/(you)/authorized_keys

```

then you should be able to log in with the ssh key.  now, with that said, it's still a good idea to have a passphrase on the certificate (unless, you're using it for a scripted process)

furthermore, if this user isn't your user (e.g. a secondary user just for FTP, or something of that nature), it would be a good idea to lock the password to disable password-based logins (sudo passwd -l <username>)

just don't do this to your user, else you'll not be able to elevate your privileges ...

---

