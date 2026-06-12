---
title: "Network two machines over the internet"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-02-27
Hello all, 

Me and my friend have been talking about networking our two machines over the internet. So he has done his side. Now i need to do my side... Any ideas on how i would go about configuring my computer to do this? 

Thanks guys, 
SlashWannabe94

---

### Post by slashwannabe94 on 2011-02-27
Preferably using VPN :)

---

### Post by spiky001 on 2011-02-27
What do yo wish to achieve file transfer? gaming?

---

### Post by slashwannabe94 on 2011-02-27
File sharing. Using each others resources. Sort of like a remote desktop connection, but the ability to utilize the machine as i would with my own. 

You get where i am at dude?

---

### Post by spiky001 on 2011-02-27
You can use ssh

---

### Post by slashwannabe94 on 2011-02-27
I know i could use ssh dude, but how would i go about connecting my machine to his over the internet. ssh would be perfect :D 

I have never networked a machine over the internet though :/ 

Thats my downfall, and was hoping you guys could help me with that. 

Thanks, 

SlashWannabe94

---

### Post by spiky001 on 2011-02-27
Both machines need open sssh server installed, Then you need to allow port forwarding on routers so the ssh port is visible to outside internetset firewall to allow incoming connection on ssh port this might help [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by slashwannabe94 on 2011-02-27
I have edited my /etc/ssh/sshd_config file to look like this

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
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

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
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue

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
AllowTcpForwarding no
AllowUsers marcom sherron

-------------------------------------------------------

I have done that, so what do i need to do now?

---

### Post by spiky001 on 2011-02-27
You have to set the router to allow port forwarding as well

---

### Post by movieman on 2011-02-27
Best solution would probably be to set up OpenVPN to create a VPN between the two systems: then they would appear to be on the same network and everything should work.

You can forward ports through ssh, but it's more complex as you need to know all the ports to forward.

---

