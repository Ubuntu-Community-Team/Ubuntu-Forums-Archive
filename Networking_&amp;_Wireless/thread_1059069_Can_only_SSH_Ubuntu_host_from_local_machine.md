---
title: "Can only SSH Ubuntu host from local machine"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by tommy1987 on 2009-02-03
Hi,

I have installed and configured (I think) SSH for Ubuntu Intrepid Ibex. I can ssh into my machine when on my local machine. If I try this from anywhere external, I get a timeout. I can successfully ping the machine though.

My /etc/ssh/shhd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 222
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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

UsePAM yes
```


Is there something I have missed?

Thanks,
Tom

---

### Post by Calmatory on 2009-02-03
Is port 22 forwarded properly?

---

### Post by fs3rp4 on 2009-02-03
Try to nmap the external IP. The TCP port 22 must be open.




> **tommy1987 said:**
> Hi,

I have installed and configured (I think) SSH for Ubuntu Intrepid Ibex. I can ssh into my machine when on my local machine. If I try this from anywhere external, I get a timeout. I can successfully ping the machine though.

My /etc/ssh/shhd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 222
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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

UsePAM yes
```


Is there something I have missed?

Thanks,
Tom

---

### Post by tommy1987 on 2009-02-03
There is no problem with port forwarding since this problem still occurs when on the local network but a different machine.

I give the local IP like so (from another host on the very same network):

ssh -p 222 tom@192.168.1.14

A ping to that address works without a problem.

Thanks,

---

### Post by mattman85 on 2009-02-03
have you tried doing it by host-name if possible?

---

### Post by Iowan on 2009-02-03
Firewall active?  From the looks of things I presume that by "local" you mean localhost, and "remote" means another machine on the same network.  It also appears you are using port 222 instead of port 22 (should still work - I do that on my router). As I read your post, you are not trying to SSH into the machine from internet? Is this accurate, or did I miss something?

---

### Post by mattman85 on 2009-02-03
also...  you could always try using [PuTTY]("http://putty.org") just to check if its the terminal..  if you want something for on-the-go, [PortableApps]("http://portableapps.com") has PuTTY Portable for usb devices.  I've had issues with ssh through command line when I'm at work, and PuTTY hasn't failed me yet.

---

