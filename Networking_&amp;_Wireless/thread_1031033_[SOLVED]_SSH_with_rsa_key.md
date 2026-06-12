---
title: "[SOLVED] SSH with rsa key"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by cdmike2k8 on 2009-01-04
I ma trying to connect to a server through ssh with rsa key authentication. I already created the key and moved the public one to the server authorized_keys folder.  I followed this [guide http://ubuntuforums.org/showthread.php?t=904796]("http://ubuntuforums.org/showthread.php?t=904796").  Here is the output of ssh -v ```
debug1: Connecting to server [1.1.1.1] port 22.
debug1: Connection established.
debug1: identity file /home/michael/.ssh/identity type -1
debug1: identity file /home/michael/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/michael/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[server]:22' is known and matches the RSA host key.
debug1: Found key in /home/michael/.ssh/known_hosts:5
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/michael/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/michael/.ssh/identity
debug1: Trying private key: /home/michael/.ssh/id_dsa
debug1: Next authentication method: password
```
I changed the server name, port and ip address for security.  Any help would be appreciated.

---

### Post by kevdog on 2009-01-05
Can you post your sshd conf file along with checking your hosts.allow and hosts.deny file?

---

### Post by cdmike2k8 on 2009-01-05
here is the ssh config (/etc/ssh/ssh_config): ```
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
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```
If it helps, I don't use port 22, but a different one, ```
ssh -p port host
``` works fine.  Where would I get allowed and denyed hosts?

---

### Post by dmizer on 2009-01-05
ssh_conf != sshd_conf ;)

ssh_conf is the configure file for the client portion of ssh.
sshd_conf is the configure file for the server portion of ssh. Since you are having trouble connecting to your server, we'll need to see the server configure file.

> **cdmike2k8 said:**
> Where would I get allowed and denyed hosts?
These are located in /etc/

/etc/hosts.allow
/etc/hosts.deny

---

### Post by cdmike2k8 on 2009-01-05
ok, here is the **sshd** file ```
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

UsePAM yes
```
hosts.allow```
 /etc/hosts.allow: list of hosts that are allowed to access the system.
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
hosts.deny```
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

---

### Post by dmizer on 2009-01-05
Okay, uncomment this option:
```
#AuthorizedKeysFile	%h/.ssh/authorized_keys
```
This shouldn't matter, but you never know.

Once you make changes, restart the ssh server:
```
sudo /etc/init.d/ssh restart
```

The rest looks okay, though you may want to disable pam (once you get RSA working of course):
```
UsePAM no
```

Please attempt to connect, then post the output of:
```
cat /var/log/auth.log | grep sshd
```

---

### Post by cdmike2k8 on 2009-01-05
output of cat... ```

Jan  4 21:58:48 fileserv sshd[1291]: User michael authorized keys /home/michael/.ssh/authorized_keys is not a regular file
Jan  4 21:58:48 fileserv sshd[1291]: User michael authorized keys /home/michael/.ssh/authorized_keys is not a regular file
Jan  4 21:58:53 fileserv sshd[1291]: Accepted password for michael from 169.231.10.147 port 39733 ssh2
Jan  4 21:58:53 fileserv sshd[1291]: pam_unix(sshd:session): session opened for user michael by (uid=0)
Jan  4 21:59:21 fileserv sudo:  michael : TTY=pts/2 ; PWD=/home/michael ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Jan  4 21:59:52 fileserv sshd[3884]: Received signal 15; terminating.
Jan  4 21:59:52 fileserv sshd[1394]: Server listening on :: port 1988.
Jan  4 21:59:52 fileserv sshd[1394]: Server listening on 0.0.0.0 port 1988.
Jan  4 22:00:00 fileserv sshd[1291]: pam_unix(sshd:session): session closed for user michael
Jan  4 22:00:12 fileserv sshd[1477]: User michael authorized keys /home/michael/.ssh/authorized_keys is not a regular file
Jan  4 22:00:19 fileserv sshd[1477]: Accepted password for michael from 169.231.10.147 port 39736 ssh2
Jan  4 22:00:19 fileserv sshd[1477]: pam_unix(sshd:session): session opened for user michael by (uid=0)

```

---

### Post by kevdog on 2009-01-05
What are the permissions on the ~/.ssh/authorized_keys file?

ls -la ~/.ssh/authorized_keys

---

### Post by cdmike2k8 on 2009-01-05
```
-rw-r--r-- 1 michael michael  745 2009-01-04 20:30 id_rsa_local.pub

```

---

### Post by dmizer on 2009-01-05
Well, the permissions are set right.

How about the formatting? The key itself should be on one entire line, like so:
```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAtfPmSfqOj5cNPBGdEX+PDgA/lvOOXP0hBu48Cwt0bAm-rest-of-key== user@client
```

And not like this:
```
ssh-rsa 
AAAAB3NzaC1yc2EAAAABIwAAAQEAtfPmSfqOj5cNPBGdEX+PDgA/lvOOXP0hBu48Cwt0bAm-rest-of-key== 
user@client
```

---

### Post by cdmike2k8 on 2009-01-05
Thats how it is formatted.  Any other ideas? Just to make sure, you generate the key on the client, not the server, right?

---

### Post by dmizer on 2009-01-05
> **cdmike2k8 said:**
> Thats how it is formatted.  Any other ideas? Just to make sure, you generate the key on the client, not the server, right?

That is correct, and you copy the contents of the clients id_rsa.pub into authorized_keys

Is the client Windows or Linux? If Windows, what software are you using?

---

### Post by dmizer on 2009-01-05
Humm, if your client is Linux, I just found an interesting tool.

Try this:

1) remove the current authorized_keys file from the server
```
rm ~/.ssh/authorized_keys
```
2) send your rsa key to the server via the ssh tool as follows:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@server
```

"ssh-copy-id" should set all permissions correctly on both the directory and the authorized_keys file. This way, you are absolutely positive that the "authorized_keys" is correct.

---

### Post by cdmike2k8 on 2009-01-05
> **dmizer said:**
> Humm, if your client is Linux, I just found an interesting tool.

Try this:

1) remove the current authorized_keys file from the server
```
rm ~/.ssh/authorized_keys
```
2) send your rsa key to the server via the ssh tool as follows:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@server
```

"ssh-copy-id" should set all permissions correctly on both the directory and the authorized_keys file. This way, you are absolutely positive that the "authorized_keys" is correct.
Thanks so much, this solved the problem!

---

### Post by dmizer on 2009-01-05
Fantastic! By the way, I found that tool in the Ubuntu wiki on SSH here: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

And specifically here: [https://help.ubuntu.com/community/AdvancedOpenSSH#Locating%20the%20Keys%20on%20Remote%20Computers](https://help.ubuntu.com/community/AdvancedOpenSSH#Locating%20the%20Keys%20on%20Remote%20Computers)

Just used the tool to convert my network from DSA to RSA (been meaning to do that for a long time, thanks for lighting the fire ;))

---

### Post by kevdog on 2009-01-06
dmizer

Awesome find.  Never heard of that utility -- great investigation.

---

