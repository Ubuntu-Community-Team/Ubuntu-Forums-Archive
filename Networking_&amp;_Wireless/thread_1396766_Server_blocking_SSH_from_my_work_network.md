---
title: "Server blocking SSH from my work network"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by innerspaceproductions on 2010-02-02
I have an ubuntu 8.04 dedicated server running openssh which I am having problems with.

The server is based in England yet I am currently working from Thailand. Slow speeds and timeouts I am used to but it is now over 24hr since I have managed to SSH the server (from here).

I just tried remote desktop on my PC back in the UK and this connected straight away through both SSH and SCP.

Thinking that it may be the IP being blocked from my works network I switched off wifi on my phone and tried to connect over the data network a few times with no luck.

Another strange problem is that when we got the server it was locked into a chroot jail which SSH(22) always leads into. After accessing SSH on port 22 I have to run a break script to gain root access.
The sshd_config file says that the server is listening on port 57 yet I have never been able to access this.

I am running out of ideas on what the cause/solution of this is - any help will be appreciated.

```

> netstat -a | grep ssh
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
> iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:20000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3s 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp-data 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination             

```

/etc/ssh/sshd_config
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 57
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
DenyGroups deniedssh

```


/etc/hosts.deny
```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

/etc/hosts.allow
```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#

```

---

### Post by innerspaceproductions on 2010-02-02
I did a couple more tests, connecting to another server from my home network and connecting to my server from a web SSH client, both of which worked.

This led me to believe that it was definitely my server refusing the connections.

I probed around the server a little more and found another set of hosts.allow and hosts.deny in /usr/fs/etc/ - which is where the chroot locks me with SSH until I break out.

Here I found my ip address and moving it from deny to allow regained access.

So my new problem - how do I get SSH to connect me to the servers root instead of this chroot?

The chroot is listening on port 22 yet the main service appears to be listening on port 57(see above) - yet I have been unable to establish a connection on port 57 no matter what I try.

---

