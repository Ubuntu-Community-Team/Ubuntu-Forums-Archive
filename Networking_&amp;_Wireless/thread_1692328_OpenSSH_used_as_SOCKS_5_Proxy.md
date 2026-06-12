---
title: "OpenSSH used as SOCKS 5 Proxy"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by ffix411 on 2011-02-21
Hi,
First i'll explain you why do i have to use a proxy, and then i'll explain u my troubles =)

I'm playing a game, (named silkroad if someone knows x)), and now, you can connect only 2 games per ip (public one).

So i thought : why not to run a socks 5 proxy on my notebook which is connected to another gateway (my neighboors' one xD)

Then i've found a soft which allow my game to connect through a socks5 proxy.
And after some googling i've also found that OpenSSH does support the socks 5.

I've set my OpenSSH server, and tried to connect my game through the proxy.

And here is the error : 

> 
[14:17:18] Starting "C:\Program Files (x86)\Silkroad\sro_client.exe /18 0 2"
[14:17:23] Connecting to loginserver 'gwgt3.joymax.com (121.128.133.28)'...
[14:17:23] Connecting to proxy...
[14:17:23] Successfully connected to proxy
[14:19:24] ERROR: Cannot connect to loginserver [-4]
[14:19:24] The proxy did not accept the connection request [0]
[14:19:24] Stop training

So i guess, i'm connected to the proxy, but it's like if OpenSSH does not forward the game's login server connection to the remote gateway (the neighboors' one)

Game works on the notebook (when ran directly on it)
Game works through public proxies found on the internet (but unfortunately most of them aren't stable at all) 
Port 22 is open both in the gateway firewall and NAT

So, i'm lost and need some help ^^ (it's the first time i try to set up a SOCKS 5 proxy serv)

I leave the "sshd_config" below :
> 
#    $OpenBSD: sshd_config,v 1.82 2010/09/06 17:10:19 naddy Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/bin:/usr/sbin:/sbin:/usr/bin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# The default requires explicit activation of protocol 1
#Protocol 2

# HostKey for protocol version 1
#HostKey /etc/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh_host_rsa_key
#HostKey /etc/ssh_host_dsa_key
#HostKey /etc/ssh_host_ecdsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 1024

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
StrictModes no
MaxAuthTries 3
#MaxSessions 10

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile    .ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh_known_hosts
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
PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

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
UsePAM no


AllowAgentForwarding yes
AllowTcpForwarding yes
GatewayPorts yes
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
UseLogin no
UsePrivilegeSeparation yes
PermitUserEnvironment yes
Compression delayed
ClientAliveInterval 0
ClientAliveCountMax 3
UseDNS yes
PidFile /var/run/sshd.pid
MaxStartups 10
PermitTunnel yes
#ChrootDirectory none

# no default banner path
#Banner none

# override default of no subsystems
#Subsystem    sftp    /usr/sbin/sftp-server

# Example of overriding settings on a per-user basis
Match User anoncvs
    X11Forwarding yes
    AllowTcpForwarding yes
    ForceCommand cvs server
Thanks-

---

