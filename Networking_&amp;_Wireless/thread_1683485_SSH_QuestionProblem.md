---
title: "SSH Question/Problem"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by silvagroup on 2011-02-07
Have Openssh installed and trying to SSH into my desktop from my Andorid based phone.
Firewall is set up and I get to the desktop but will not match pub keys and continues to ask for ath password which I dont even have set up.
What I am missing here:
# Package generated configuration file
# See the sshd(8) manpage for details

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

RSAAuthentication no
PubkeyAuthentication no
# AuthorizedKeysFile %h/.ssh/authorized_keys

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
#PasswordAuthentication no

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

UsePAM yes
UseDNS no
#AllowUsers demo

---

### Post by Brandon Williams on 2011-02-08
I think that you want:```
PubkeyAuthentication yes
PasswordAuthentication no
```

---

### Post by silvagroup on 2011-02-09
Thanks now after changing to suggested, restarting ssh and trying to get to server I get:
your host doesn't support "password" or "keyboard-interactive" authentication.

---

### Post by Brandon Williams on 2011-02-10
Comment out the "PasswordAuthentication" setting until you get pubkey authentication working.

If you run ssh with the -v option, it should give you a whole bunch of output related to what it's trying to do. Is it trying to use the key(s) that you expect it to try? If it's trying but failing, double check ~/.ssh/authorized_keys on the server. If it's not even trying, then make sure that the keys are correctly loaded into your key agent or specified on the comment line.

---

### Post by silvagroup on 2011-02-11
Thanks Brandon but can't run ssh with the -v option form my Android phone doesn't really have ssh. I am trying to connect with conectbot.
From what I have seen there is an ssh for android called dropbear or something similar to that, really need to learn more about this whole android os, it ain't exactly our beloved Gnu/Linux.

So I am not sure what is happening on the phone side. Can't wait till I can figure out android better so I can get past all these annoying issues.

From your responses I am thinking I have an issue with my passwords as soon as I finish my tasks for today am going to regen the passwords and try again.A careful look at my sshd config shows that I have dsa auth and I think my regen was rda.

Will post back with results.
Thanks for your continued help !!!!

---

