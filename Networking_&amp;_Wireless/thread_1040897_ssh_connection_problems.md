---
title: "ssh connection problems"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by justinhj on 2009-01-16
I've had trouble connecting to my ubuntu box from outside the local network. Port forwarding to the port ssh is running in is working. And I can connect to the port if I run a different kind of server on it. But running sshd, when I connect, it stalls at this point every time...

debug1: Local version string SSH-2.0-OpenSSH_5.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent

I can connect from ssh on another computer inside the network, just not from outside.

ssh -vvv -p (port) (my login)@(my ip)


Any clues to diagnose?

justinhj

> 
# What ports, IPs and protocols we listen for
# Use these options to restrict which interfaces/protocols sshd will bind to
Port 2009
ListenAddress 192.168.0.103
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
ChallengeResponseAuthentication yes

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
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes

#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

AllowTcpForwarding yes

GatewayPorts yes




---

### Post by justinhj on 2009-01-18
Just an update, I wondered if Protocol 1 would work, so I set that up, and it still stalls at what looks to me like the same stage of authentification.

> debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type 0
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Local version string SSH-1.5-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: Waiting for server public key.

I've seen some problems related to the router killing or damaging certain kinds of packets. Does anyone know more about that? I'm out of ideas.

justinhj

---

