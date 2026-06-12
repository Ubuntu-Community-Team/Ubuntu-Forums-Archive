---
title: "port 22: Connection refused always..."
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by tdheff on 2010-06-24
Hi, I am trying to set up an ssh server on my home computer so that I can access it from work. I forwarded port 22 from my router (apple airport extreme) and got my rsa keys ready and thought I was going to be good to go until I checked my server ($ ssh localhost) and got the message: > ssh: connect to host localhost port 22: Connection refused
I tried to open the ports on my firewall (using firestarter) and I looked this up but no one's solutions seemed to work for me.

Please help!

---

### Post by VH-BIL on 2010-06-24
There are 4 possible things causing this.

1) Port forwarding in your router is incorrect.
2) Firewall issues.
3) ssh server is not running.
4) ssh is set to a different port.

When trying it locally it would be one of the last 3.

---

### Post by tdheff on 2010-06-24
"ps aux | grep ssh" returns: > root       916  0.0  0.0   5548   912 ?        Ss   18:17   0:00 /usr/sbin/sshd
tommy     2190  0.0  0.0   3280   360 ?        Ss   18:18   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
tommy     2853  0.0  0.0   3324   888 pts/0    S+   19:04   0:00 grep --color=auto ssh


"cat /etc/services | grep 22" returns: > ssh		22/tcp				# SSH Remote Login Protocol
ssh		22/udp

Does that help a diagnosis?

---

### Post by VH-BIL on 2010-06-24
Have you tried:
ssh 127.0.0.1
ssh <Your IP>

If you are behind a firewall you can try uninstalling it to check if that is the problem (then reinstall it if you like).

---

### Post by Iowan on 2010-06-24
It might help if you could post */etc/ssh/ssh_config* and */etc/ssh/sshd_config*. Does machine have static or DHCP address. There's another thread around (somewhere) that mentions SSH being picky about permissions of some directories...

---

### Post by tdheff on 2010-06-24
The ip address is static. On an interesting note, /etc/init.d/sshd does not exist.
> # Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 7777
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


> # This is the ssh client system-wide configuration file.  See
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
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no


---

### Post by Iowan on 2010-06-25
The server is listening on port 7777, but the client is using port 22?

---

### Post by tdheff on 2010-06-26
That solved it! I changed that and the ServerBitsKey to 1024 and it worked fine.

---

### Post by itagomo on 2012-09-14
please post steps ..

---

