---
title: "iptables and ssh"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by GSF1200S on 2009-10-01
Im having issues getting iptables to allow an inbound connection for ssh. I have port forwarding enabled on my router, and can access the machine via ssh when iptables is stopped.

The rule I used to allow the connection is:
```
iptables -A open -p tcp --dport 26 -j ACCEPT
```

I have sshd setup to use port 26 rather than port 22. Even in a local network setting, I cannot get a connection. 

My /etc/ssh/ssh_config is as follows:
```
#	$OpenBSD: ssh_config,v 1.25 2009/02/17 01:28:32 djm Exp $

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
   Port 26
   Protocol 2
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
HashKnownHosts yes
StrictHostKeyChecking ask
```

And my /etc/ssh/sshd_config:
```
#	$OpenBSD: sshd_config,v 1.80 2008/07/02 02:24:18 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

Port 26
#AddressFamily any
ListenAddress 0.0.0.0
#ListenAddress ::

# Disable legacy (protocol version 1) support in the server for new
# installations. In future the default will change to require explicit
# activation of protocol 1
Protocol 2

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 1024

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 120
#PermitRootLogin no
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile	.ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
ChallengeResponseAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

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

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10
#PermitTunnel no
#ChrootDirectory none

# no default banner path
Banner /etc/issue

# override default of no subsystems
Subsystem	sftp	/usr/lib/ssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	ForceCommand cvs server
AllowUsers    username (I actually have my username here)
```

And finally the printout from iptables -nvL. When I setup iptables I didnt realize I could setup rules for all interfaces, so I set the rules for each interface individually:
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 18 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 17 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 10 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 9 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 9 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 5 
    0     0 DROP       all  --  wlan0  *       127.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  eth1   *       127.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  eth0   *       127.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  wlan0  *       192.168.0.0/16       0.0.0.0/0           
    0     0 DROP       all  --  eth1   *       192.168.0.0/16       0.0.0.0/0           
    0     0 DROP       all  --  eth0   *       192.168.0.0/16       0.0.0.0/0           
    0     0 DROP       all  --  eth1   *       172.16.0.0/12        0.0.0.0/0           
    0     0 DROP       all  --  wlan0  *       172.16.0.0/12        0.0.0.0/0           
    0     0 DROP       all  --  eth0   *       172.16.0.0/12        0.0.0.0/0           
    0     0 DROP       all  --  wlan0  *       10.0.0.0/8           0.0.0.0/0           
    0     0 DROP       all  --  eth1   *       10.0.0.0/8           0.0.0.0/0           
    0     0 DROP       all  --  eth0   *       10.0.0.0/8           0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   71 58876 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 interfaces  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 open       all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
    0     0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:!0x17/0x02 state NEW 
    0     0 DROP       all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
    0     0 DROP       icmp --  eth0   *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 DROP       icmp --  eth1   *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 DROP       icmp --  wlan0  *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:26 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 30 packets, 1236 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain interfaces (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           

Chain open (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  foo    *       0.0.0.0/0            0.0.0.0/0           tcp dpts:65000:65005 
    0     0 ACCEPT     tcp  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           tcp dpts:65000:65005 
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:65000:65005 
    0     0 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:65000:65005 
    0     0 ACCEPT     udp  --  foo    *       0.0.0.0/0            0.0.0.0/0           udp dpts:65000:65005 
    0     0 ACCEPT     udp  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           udp dpts:65000:65005 
    0     0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp dpts:65000:65005 
    0     0 ACCEPT     udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp dpts:65000:65005 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:26 

```

Any ideas, or criticisms of my setup are welcome :)

---

### Post by Torrance on 2009-10-15
I just randomly came across this question while googling to solve my own iptables questions, and seeing its only a week old thought I'd have a stab at fixing your problem.

Try this instead (substitute 'open' with 'input'):

```
iptables -A INPUT -p tcp --dport 26 -j ACCEPT
```

...and that might get things working for you.

---

### Post by JKyleOKC on 2009-10-15
I'd check closely that one rule that's getting all of the packets and bytes (the leftmost two columns in the iptables report). You might move it to come AFTER the rule to send packets to "open" instead of before as it is now, since any rule that jumps to ACCEPT will prevent all following rules from being tested, if it matches.

I also prefer to set a policy of DROP and then just accept the specific ports I need, since having individual rules jump to DROP can easily cause such mysterious problems.

---

