---
title: "sshfs connection reset by peer"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by tucemiux on 2010-01-26
I am using ssh with public keys and one user is unable to mount a shared partition.  I am able to mount the same directory remotely locally and over the internet but the other user keeps getting the same error every time he attempts to mount the partition using sshfs, locally or outside from the internet.

The user can log in to my file server remotely and from the internet using ssh and has access to the directory but sshfs gives the same error: sshfs connection reset by peer

Is it possible a firewall is denying access through sshfs?  I have given the user permission to mount local drives on the file server and added the user to the "fuse" group.  Why is the user unable to mount the shared partition?

This is the command that fails:

sshfs 192.168.1.100:/media/hd /media/shared_drive

Below is my sshd_config:

 Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
#Port 22
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
PasswordAuthentication no

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

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

#Users to allow
AllowUsers one two
Port 9090

---

### Post by Lars Noodén on 2010-01-27
> **tucemiux said:**
> I am using ssh with public keys and one user is unable to mount a shared partition.  I am able to mount the same directory remotely locally and over the internet but the other user keeps getting the same error every time he attempts to mount the partition using sshfs, locally or outside from the internet.


Does he get it immediately or does it happen after a longer while?

> **tucemiux said:**
> 

The user can log in to my file server remotely and from the internet using ssh and has access to the directory but sshfs gives the same error: sshfs connection reset by peer

Is it possible a firewall is denying access through sshfs? 


sshfs uses SFTP which is part of SSH and thus uses the same ports and protocol as SSH.

Can he connect using sftp?  If not, sshfs won't work.  

Are you both connecting from the same LAN?

**Allow Groups** is an easier way to manage who can log in than **Allow Users**.  You can add or remove access by using the regular system tools and thus do not need to edit sshd_config or restart to make these changes.  You can also add many more users via groups before it gets unwieldy.

---

### Post by johnson.d on 2010-01-28
This will give you additional debugging output

$ sshfs -o sshfs_debug user@server <mountpoint>

---

### Post by tucemiux on 2010-02-13
thank you for your input.  If I have time I will try using the debug options.  The obvious quick fix was to just enable password login so now I have both enabled, key and password.

---

### Post by marshcast on 2011-01-23
For anyone still trying to find a reason for this, I found that i didn't have perms for the dir i was trying to mount to.

because of that I tried to 'sudo' the command.

that was my problem.

had to NOT sudo sshfs, and make the mountpiont something I had permissions for.

good luck ;)

---

