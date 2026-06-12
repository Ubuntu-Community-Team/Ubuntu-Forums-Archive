---
title: "SSH Without Password Between Ubuntu and Cygwin"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by dudemanbubba on 2013-04-16
I have exhausted all efforts that I know of to get this working.  We have a remote satellite office that we are trying to back the server up to our main office to provide off-site backups.  For the purposes of this discussion, the remote is the server I am backing up and the local is the backup server at my location.  I have run through about 30 different tutorials on how to set it up and have not had any success.  In most instances, I created the ssh keys on the local machine, copied the keys to the remote machine in the .ssh folder and then added it into the authorized keys files in the remote .ssh folder using:

```
$cat mykeyname.pub >> authorized_keys
$cat mykeyname.pub >> authorized_keys2
```

When I check the contents of the authorized_key files the key is in there.  I have made sure that the authorized_key files are chmod 600 (or 640 as some of the tutorials have suggested).  I have made sure the .ssh folder is chmod 700.

All of the programs work as expected with the exception of it continuing to require the entering of a password.  I need this to be an automated backup process so I am looking for some assistance from anyone who can help.  I have included my ssh configurations on both the remote and local machines below.  Any help is appreciated.



Remote Server:
Ubuntu Server 10.04 LTS
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
rsync version 3.0.7 protocol version 30

Remote SSH Config:

```
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
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
RSAAuthentication yes
PasswordAuthentication no
PubkeyAuthentication yes   
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
#   Port 22
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

```
Local Backup Server:
Cygwin 1.7.15
OpenSSH_6.2p1, OpenSSL 1.0.1e 11 Feb 2013
rsync version 3.0.9 protocol version 30

Local SSH Config:

```
$ cat ssh_config
#       $OpenBSD: ssh_config,v 1.26 2010/01/11 01:39:46 dtucker Exp $


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


# Host *
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
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com

```

---

### Post by Slim Odds on 2013-04-16
Is your secret key in the .ssh directory in cygwin?
Is the cygwin .ssh directory also chmod 700?

---

### Post by dudemanbubba on 2013-04-16
Yes on both counts.

The file permissions for the .ssh folder for the local machine are:

```
drwx------+ 1 Administrator None    0 Apr 16 13:00 .ssh
```

and the files contained within .ssh are:

```
-rw------- 1 Administrator None 668 Apr 16 12:17 administrator-rsync-key
-rw------- 1Administrator None 609 Apr 16 12:17 administrator-rsync-key.pub
-rw-r--r-- 1 Administrator None 587 Apr 16 12:37 known_hosts
```



The files permissions for the .ssh folder for the remote machine are:

```
drwx------  2 administrator administrator     4096 2013-04-16 12:04 .ssh
```

and the files contained with .ssh are:

```
-rw------- 1 administrator administrator  609 2013-04-16 12:04 administrator-rsync-key.pub
-rw-r--r-- 1 administrator administrator 2020 2013-04-16 12:28 authorized_keys
-rw-r--r-- 1 administrator administrator 1243 2013-04-16 12:04 authorized_keys2
```

---

### Post by Slim Odds on 2013-04-16
It's even better to use the 'stat' command to look at the permissions.

---

### Post by dudemanbubba on 2013-04-17
Not sure if there is any new information from the stat command...

Local machine .ssh files:

```
$ stat *
  File: `administrator-rsync-key'
  Size: 668             Blocks: 4          IO Block: 65536  regular file
Device: 3e4cd3a6h/1045222310d   Inode: 20829148276707877  Links: 1
Access: (0600/-rw-------)  Uid: (  500/Administrator)   Gid: (  513/    None)
Access: 2013-04-16 12:17:45.674724000 -0400
Modify: 2013-04-16 12:17:45.674724000 -0400
Change: 2013-04-16 12:18:13.800442200 -0400
 Birth: 2013-04-16 12:17:45.674724000 -0400
  File: `administrator-rsync-key.pub'
  Size: 609             Blocks: 4          IO Block: 65536  regular file
Device: 3e4cd3a6h/1045222310d   Inode: 81909218222921475  Links: 1
Access: (0600/-rw-------)  Uid: (  500/Administrator)   Gid: (  513/    None)
Access: 2013-04-16 12:17:45.674724000 -0400
Modify: 2013-04-16 12:17:45.674724000 -0400
Change: 2013-04-16 12:18:13.800442200 -0400
 Birth: 2013-04-16 12:17:45.674724000 -0400
  File: `known_hosts'
  Size: 587             Blocks: 1          IO Block: 65536  regular file
Device: 3e4cd3a6h/1045222310d   Inode: 33495522228692136  Links: 1
Access: (0644/-rw-r--r--)  Uid: (  500/Administrator)   Gid: (  513/    None)
Access: 2013-04-16 12:19:06.651209400 -0400
Modify: 2013-04-16 12:37:55.590546200 -0400
Change: 2013-04-16 12:37:55.590546200 -0400
 Birth: 2013-04-16 12:19:06.651209400 -0400

```

Remote server .ssh files:

```
administrator@dcls1:~/.ssh$ sudo stat *
[sudo] password for administrator: 
  File: `administrator-rsync-key.pub'
  Size: 609           Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d    Inode: 6553682     Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/administrator)   Gid: ( 1000/administrator)
Access: 2013-04-16 12:04:59.690568007 -0400
Modify: 2013-04-16 12:04:52.989318287 -0400
Change: 2013-04-16 12:34:20.739318214 -0400
  File: `authorized_keys'
  Size: 2020          Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d    Inode: 6553675     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/administrator)   Gid: ( 1000/administrator)
Access: 2013-04-16 12:33:35.659318495 -0400
Modify: 2013-04-16 12:28:03.533068514 -0400
Change: 2013-04-16 15:14:57.099318128 -0400
  File: `authorized_keys2'
  Size: 1243          Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d    Inode: 6553676     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/administrator)   Gid: ( 1000/administrator)
Access: 2013-04-08 15:42:16.239318199 -0400
Modify: 2013-04-16 12:04:59.690568007 -0400
Change: 2013-04-16 15:14:51.396491457 -0400


```

---

### Post by Slim Odds on 2013-04-17
What about stat for the .ssh directory itself?

---

### Post by steeldriver on 2013-04-17
Did you create the key pair with an empty passphrase? are you sure it is the server asking you for a password - not the client asking for the passphrase for your private key?

---

### Post by dmn_clown on 2013-04-18
> **dudemanbubba said:**
> 

Remote SSH Config:

```
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
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
RSAAuthentication yes
PasswordAuthentication no
PubkeyAuthentication yes   
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
#   Port 22
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

```

What about sshd_config?  You've given the config for the client which is useless for what you want others to double check for you.

Beyond that, there is probably just a syntax error in your key.  Use the ssh-copy-id script provided with cygwin's ssh to copy your key rather than manually copying the file.

```
ssh-copy-id -i /path/to/ssh/id_rsa.pub remote-host
```

---

### Post by dudemanbubba on 2013-04-18
> **steeldriver said:**
> Did you create the key pair with an empty passphrase? are you sure it is the server asking you for a password - not the client asking for the passphrase for your private key?

Yes.  I had an empty passphrase.  It is definitely asking for the password since I enter it to move on and it continues.

---

### Post by dudemanbubba on 2013-04-18
Here is the sshd_config on the remote server:

```
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
LogLevel INFO


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

```

---

### Post by dudemanbubba on 2013-04-18
Here is the output when I include -vv debug option.  Maybe this will provide some insight...

```
$ ssh -vv administrator@192.168.5.101
OpenSSH_6.2p1, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.5.101 [192.168.5.101] port 22.
debug1: Connection established.
debug1: identity file /home/Administrator/.ssh/id_rsa type -1
debug1: identity file /home/Administrator/.ssh/id_rsa-cert type -1
debug1: identity file /home/Administrator/.ssh/id_dsa type -1
debug1: identity file /home/Administrator/.ssh/id_dsa-cert type -1
debug1: identity file /home/Administrator/.ssh/id_ecdsa type -1
debug1: identity file /home/Administrator/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH_5*
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 119/256
debug2: bits set: 532/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 0e:fd:6f:52:d8:a2:be:ae:ff:1f:5e:9d:c1:95:24:d1
debug1: Host '192.168.5.101' is known and matches the RSA host key.
debug1: Found key in /home/Administrator/.ssh/known_hosts:1
debug2: bits set: 516/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/Administrator/.ssh/id_rsa (0x0),
debug2: key: /home/Administrator/.ssh/id_dsa (0x0),
debug2: key: /home/Administrator/.ssh/id_ecdsa (0x0),
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/Administrator/.ssh/id_rsa
debug1: Trying private key: /home/Administrator/.ssh/id_dsa
debug1: Trying private key: /home/Administrator/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
administrator@192.168.5.101's password:

```

---

### Post by dudemanbubba on 2013-04-19
Well... I started over one more time.  I erased the previous key files (i.e. *.pub, etc) files on the local machine.  I removed the authorized key files from the remote machine.  Made no changes to any of the config files.  I created new keys on the local machine then ran ssh-copy-id and now everything appears to be working.  I had done this before so I have no idea why...

Regardless, thank you all for your suggestions.

---

### Post by dudemanbubba on 2013-04-19
Thanks again!

---

### Post by Slim Odds on 2013-04-19
They call this PBKAC :)

---

