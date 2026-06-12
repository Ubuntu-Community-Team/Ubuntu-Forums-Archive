---
title: "public key authentication fails"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by digitrev on 2010-02-06
I'm trying to connect to my Xubuntu box (zelda) remotely using my RSA key. I'm using Cygwin on my Windows box (link) to SSH in to the Xubuntu box. I've created the key and placed it in the authorized_keys file on my remote box. Here's where it gets weird. When I ssh into zelda the first time, it prompts me for my password. However, if I'm already connected to zelda and try to open another connection, it prompts me for my RSA passphrase. This is very confusing, and I have no idea what's going on.

Here's my sshd_config file on zelda.
```

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
AuthorizedKeysFile    %h/.ssh/authorized_keys

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

```Here's a dump of the first attempt to ssh into zelda (no connections currently open)

```

OpenSSH_5.3p1, OpenSSL 0.9.8l 5 Nov 2009
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for zelda
debug1: Connecting to zelda [192.168.0.197] port 22.
debug1: Connection established.
debug1: identity file /home/Trevor/.ssh/identity type -1
debug1: identity file /home/Trevor/.ssh/id_rsa type 1
debug1: identity file /home/Trevor/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'zelda' is known and matches the RSA host key.
debug1: Found key in /home/Trevor/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/Trevor/.ssh/identity
debug1: Offering public key: /home/Trevor/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/Trevor/.ssh/id_dsa
debug1: Next authentication method: password
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
Linux zelda 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

10 packages can be updated.
20 updates are security updates.

Last login: Sat Feb  6 09:30:28 2010 from link

trevor@zelda:~$ logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to zelda closed.
Transferred: sent 2064, received 2680 bytes, in 13.6 seconds
Bytes per second: sent 151.5, received 196.7
debug1: Exit status 0

```Here's a dump of the second attempt to ssh into zelda (one connection currently open)

```

OpenSSH_5.3p1, OpenSSL 0.9.8l 5 Nov 2009
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for zelda
debug1: Connecting to zelda [192.168.0.197] port 22.
debug1: Connection established.
debug1: identity file /home/Trevor/.ssh/identity type -1
debug1: identity file /home/Trevor/.ssh/id_rsa type 1
debug1: identity file /home/Trevor/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'zelda' is known and matches the RSA host key.
debug1: Found key in /home/Trevor/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/Trevor/.ssh/identity
debug1: Offering public key: /home/Trevor/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
Linux zelda 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

10 packages can be updated.
20 updates are security updates.

Last login: Sat Feb  6 09:33:08 2010 from link

trevor@zelda:~$ logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to zelda closed.
Transferred: sent 2560, received 2936 bytes, in 0.7 seconds
Bytes per second: sent 3497.3, received 4010.9
debug1: Exit status 0

```Does anyone know what might be going on here? Thanks in advance for any help.

---

### Post by digitrev on 2010-02-11
Hate to be that annoying guy who bumps his own threads, but I was wondering if anyone had any ideas. Thanks in advance.

---

### Post by digitrev on 2010-02-18
Any chance anybody has any ideas? I've searched around the boards and I haven't found any similar issues in the past, nor has my Google-fu revealed any tidbits of information.

---

### Post by digitrev on 2010-02-19
Anyone? This isn't a critical issue, but I would like some help if at all possible.

---

### Post by digitrev on 2010-02-21
Hate to still be bumping, but I really could use some help here.

---

### Post by digitrev on 2010-02-27
Anyone? This issue is kind of driving me up the wall. Any help or advice at all would be appreciated.

---

### Post by digitrev on 2010-03-05
Anybody? Bueller? Bueller?

---

### Post by Neezer on 2010-03-05
Have you checked your permissions on your /home/"username"/.ssh folder on the server side? sometimes if they are not correct it can cause problems.

try this

```

chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

```

---

### Post by digitrev on 2010-03-05
Thanks for the advice, but that doesn't seem to change anything.

---

### Post by Neezer on 2010-03-05
Sorry it didn't work. I'm no expert, but I had a key problem and that fixed it. I don't have any other ideas. good luck.

---

### Post by r939ick on 2010-03-05
sudo grep ssh /var/log/auth.log

and post the results.

---

### Post by digitrev on 2010-03-14
```

Mar 14 08:58:17 zelda sshd[22217]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.171.30.41  user=root
Mar 14 08:58:20 zelda sshd[22217]: Failed password for root from 203.171.30.41 port 44219 ssh2
Mar 14 09:40:24 zelda sshd[22986]: pam_sm_authenticate: Called 
Mar 14 09:40:24 zelda sshd[22986]: pam_sm_authenticate: username = [trevor] 
Mar 14 09:40:24 zelda sshd[22986]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 09:40:25 zelda sshd[22988]: Passphrase key already in keyring; rc = [1] 
Mar 14 09:40:25 zelda sshd[22988]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 09:40:25 zelda sshd[22988]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 09:40:26 zelda sshd[22988]: Passphrase key already in keyring; rc = [1] 
Mar 14 09:40:26 zelda sshd[22988]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 09:40:26 zelda sshd[22988]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 09:40:26 zelda sshd[22988]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 09:40:26 zelda sshd[22986]: Accepted password for trevor from 192.168.0.101 port 2787 ssh2
Mar 14 09:40:26 zelda sshd[22986]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 09:40:26 zelda sshd[22986]: Mount of private directory return code [0]
Mar 14 12:06:59 zelda sshd[22996]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 12:06:59 zelda sshd[22986]: pam_unix(sshd:session): session closed for user trevor
Mar 14 12:06:59 zelda sshd[22986]: Mount of private directory return code [0]
Mar 14 15:09:23 zelda sshd[27894]: pam_sm_authenticate: Called 
Mar 14 15:09:23 zelda sshd[27894]: pam_sm_authenticate: username = [trevor] 
Mar 14 15:09:23 zelda sshd[27894]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 15:09:25 zelda sshd[27896]: Passphrase key already in keyring; rc = [1] 
Mar 14 15:09:25 zelda sshd[27896]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 15:09:25 zelda sshd[27896]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 15:09:26 zelda sshd[27896]: Passphrase key already in keyring; rc = [1] 
Mar 14 15:09:26 zelda sshd[27896]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 15:09:26 zelda sshd[27896]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 15:09:26 zelda sshd[27896]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 15:09:26 zelda sshd[27894]: Accepted password for trevor from 192.168.0.101 port 4164 ssh2
Mar 14 15:09:26 zelda sshd[27894]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 15:09:26 zelda sshd[27894]: Mount of private directory return code [0]
Mar 14 15:09:28 zelda sshd[27904]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 15:09:28 zelda sshd[27894]: pam_unix(sshd:session): session closed for user trevor
Mar 14 15:09:28 zelda sshd[27894]: Mount of private directory return code [0]
Mar 14 15:09:34 zelda sshd[27916]: pam_sm_authenticate: Called 
Mar 14 15:09:34 zelda sshd[27916]: pam_sm_authenticate: username = [trevor] 
Mar 14 15:09:34 zelda sshd[27916]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 15:09:36 zelda sshd[27918]: Passphrase key already in keyring; rc = [1] 
Mar 14 15:09:36 zelda sshd[27918]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 15:09:36 zelda sshd[27918]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 15:09:37 zelda sshd[27918]: Passphrase key already in keyring; rc = [1] 
Mar 14 15:09:37 zelda sshd[27918]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 15:09:37 zelda sshd[27918]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 15:09:37 zelda sshd[27918]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 15:09:37 zelda sshd[27916]: Accepted password for trevor from 192.168.0.101 port 4167 ssh2
Mar 14 15:09:37 zelda sshd[27916]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 15:09:37 zelda sshd[27916]: Mount of private directory return code [0]
Mar 14 15:48:55 zelda sshd[29251]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:48:55 zelda sshd[29251]: Invalid user staff from 76.76.97.242
Mar 14 15:48:55 zelda sshd[29251]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:48:55 zelda sshd[29251]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:48:57 zelda sshd[29251]: Failed password for invalid user staff from 76.76.97.242 port 52969 ssh2
Mar 14 15:48:58 zelda sshd[29253]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:48:58 zelda sshd[29253]: Invalid user sales from 76.76.97.242
Mar 14 15:48:58 zelda sshd[29253]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:48:58 zelda sshd[29253]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:00 zelda sshd[29253]: Failed password for invalid user sales from 76.76.97.242 port 53365 ssh2
Mar 14 15:49:01 zelda sshd[29255]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:01 zelda sshd[29255]: Invalid user recruit from 76.76.97.242
Mar 14 15:49:01 zelda sshd[29255]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:01 zelda sshd[29255]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:03 zelda sshd[29255]: Failed password for invalid user recruit from 76.76.97.242 port 53628 ssh2
Mar 14 15:49:04 zelda sshd[29257]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:04 zelda sshd[29257]: Invalid user alias from 76.76.97.242
Mar 14 15:49:04 zelda sshd[29257]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:04 zelda sshd[29257]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:06 zelda sshd[29257]: Failed password for invalid user alias from 76.76.97.242 port 53960 ssh2
Mar 14 15:49:06 zelda sshd[29266]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:06 zelda sshd[29266]: Invalid user office from 76.76.97.242
Mar 14 15:49:06 zelda sshd[29266]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:06 zelda sshd[29266]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:09 zelda sshd[29266]: Failed password for invalid user office from 76.76.97.242 port 54282 ssh2
Mar 14 15:49:10 zelda sshd[29268]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:10 zelda sshd[29268]: Invalid user samba from 76.76.97.242
Mar 14 15:49:10 zelda sshd[29268]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:10 zelda sshd[29268]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:11 zelda sshd[29268]: Failed password for invalid user samba from 76.76.97.242 port 54653 ssh2
Mar 14 15:49:12 zelda sshd[29270]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:12 zelda sshd[29270]: Invalid user tomcat from 76.76.97.242
Mar 14 15:49:12 zelda sshd[29270]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:12 zelda sshd[29270]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:14 zelda sshd[29270]: Failed password for invalid user tomcat from 76.76.97.242 port 54937 ssh2
Mar 14 15:49:15 zelda sshd[29272]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:15 zelda sshd[29272]: Invalid user webadmin from 76.76.97.242
Mar 14 15:49:15 zelda sshd[29272]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:15 zelda sshd[29272]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:17 zelda sshd[29272]: Failed password for invalid user webadmin from 76.76.97.242 port 55251 ssh2
Mar 14 15:49:18 zelda sshd[29274]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:18 zelda sshd[29274]: Invalid user spam from 76.76.97.242
Mar 14 15:49:18 zelda sshd[29274]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:18 zelda sshd[29274]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:20 zelda sshd[29274]: Failed password for invalid user spam from 76.76.97.242 port 55579 ssh2
Mar 14 15:49:21 zelda sshd[29276]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:21 zelda sshd[29276]: Invalid user virus from 76.76.97.242
Mar 14 15:49:21 zelda sshd[29276]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:21 zelda sshd[29276]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:22 zelda sshd[29276]: Failed password for invalid user virus from 76.76.97.242 port 55958 ssh2
Mar 14 15:49:23 zelda sshd[29278]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:23 zelda sshd[29278]: Invalid user cyrus from 76.76.97.242
Mar 14 15:49:23 zelda sshd[29278]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:23 zelda sshd[29278]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:25 zelda sshd[29278]: Failed password for invalid user cyrus from 76.76.97.242 port 56198 ssh2
Mar 14 15:49:26 zelda sshd[29280]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:26 zelda sshd[29280]: Invalid user oracle from 76.76.97.242
Mar 14 15:49:26 zelda sshd[29280]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:26 zelda sshd[29280]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:28 zelda sshd[29280]: Failed password for invalid user oracle from 76.76.97.242 port 56557 ssh2
Mar 14 15:49:29 zelda sshd[29282]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:29 zelda sshd[29282]: Invalid user michael from 76.76.97.242
Mar 14 15:49:29 zelda sshd[29282]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:29 zelda sshd[29282]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:31 zelda sshd[29282]: Failed password for invalid user michael from 76.76.97.242 port 56904 ssh2
Mar 14 15:49:31 zelda sshd[29284]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:31 zelda sshd[29284]: Invalid user ftp from 76.76.97.242
Mar 14 15:49:31 zelda sshd[29284]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:31 zelda sshd[29284]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:34 zelda sshd[29284]: Failed password for invalid user ftp from 76.76.97.242 port 57199 ssh2
Mar 14 15:49:34 zelda sshd[29286]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:34 zelda sshd[29286]: Invalid user test from 76.76.97.242
Mar 14 15:49:34 zelda sshd[29286]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:34 zelda sshd[29286]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:36 zelda sshd[29286]: Failed password for invalid user test from 76.76.97.242 port 57537 ssh2
Mar 14 15:49:37 zelda sshd[29288]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:37 zelda sshd[29288]: Invalid user webmaster from 76.76.97.242
Mar 14 15:49:37 zelda sshd[29288]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:37 zelda sshd[29288]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:40 zelda sshd[29288]: Failed password for invalid user webmaster from 76.76.97.242 port 57872 ssh2
Mar 14 15:49:41 zelda sshd[29290]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:41 zelda sshd[29290]: Invalid user postmaster from 76.76.97.242
Mar 14 15:49:41 zelda sshd[29290]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:41 zelda sshd[29290]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:43 zelda sshd[29290]: Failed password for invalid user postmaster from 76.76.97.242 port 58271 ssh2
Mar 14 15:49:44 zelda sshd[29292]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:44 zelda sshd[29292]: Invalid user postfix from 76.76.97.242
Mar 14 15:49:44 zelda sshd[29292]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:44 zelda sshd[29292]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:46 zelda sshd[29292]: Failed password for invalid user postfix from 76.76.97.242 port 58629 ssh2
Mar 14 15:49:47 zelda sshd[29294]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:47 zelda sshd[29294]: Invalid user postgres from 76.76.97.242
Mar 14 15:49:47 zelda sshd[29294]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:47 zelda sshd[29294]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:48 zelda sshd[29294]: Failed password for invalid user postgres from 76.76.97.242 port 58984 ssh2
Mar 14 15:49:49 zelda sshd[29296]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:49 zelda sshd[29296]: Invalid user paul from 76.76.97.242
Mar 14 15:49:49 zelda sshd[29296]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:49 zelda sshd[29296]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:52 zelda sshd[29296]: Failed password for invalid user paul from 76.76.97.242 port 59276 ssh2
Mar 14 15:49:53 zelda sshd[29298]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:53 zelda sshd[29298]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:49:55 zelda sshd[29298]: Failed password for root from 76.76.97.242 port 59657 ssh2
Mar 14 15:49:56 zelda sshd[29300]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:56 zelda sshd[29300]: Invalid user guest from 76.76.97.242
Mar 14 15:49:56 zelda sshd[29300]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:56 zelda sshd[29300]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:49:58 zelda sshd[29300]: Failed password for invalid user guest from 76.76.97.242 port 60027 ssh2
Mar 14 15:49:59 zelda sshd[29302]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:49:59 zelda sshd[29302]: Invalid user admin from 76.76.97.242
Mar 14 15:49:59 zelda sshd[29302]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:49:59 zelda sshd[29302]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:01 zelda sshd[29302]: Failed password for invalid user admin from 76.76.97.242 port 60352 ssh2
Mar 14 15:50:01 zelda sshd[29304]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:01 zelda sshd[29304]: Invalid user linux from 76.76.97.242
Mar 14 15:50:01 zelda sshd[29304]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:01 zelda sshd[29304]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:04 zelda sshd[29304]: Failed password for invalid user linux from 76.76.97.242 port 60673 ssh2
Mar 14 15:50:05 zelda sshd[29461]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:05 zelda sshd[29461]: Invalid user user from 76.76.97.242
Mar 14 15:50:05 zelda sshd[29461]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:05 zelda sshd[29461]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:07 zelda sshd[29461]: Failed password for invalid user user from 76.76.97.242 port 32797 ssh2
Mar 14 15:50:08 zelda sshd[29463]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:08 zelda sshd[29463]: Invalid user david from 76.76.97.242
Mar 14 15:50:08 zelda sshd[29463]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:08 zelda sshd[29463]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:10 zelda sshd[29463]: Failed password for invalid user david from 76.76.97.242 port 33200 ssh2
Mar 14 15:50:11 zelda sshd[29465]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:11 zelda sshd[29465]: Invalid user web from 76.76.97.242
Mar 14 15:50:11 zelda sshd[29465]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:11 zelda sshd[29465]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:13 zelda sshd[29465]: Failed password for invalid user web from 76.76.97.242 port 33502 ssh2
Mar 14 15:50:14 zelda sshd[29476]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:14 zelda sshd[29476]: Invalid user apache from 76.76.97.242
Mar 14 15:50:14 zelda sshd[29476]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:14 zelda sshd[29476]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:15 zelda sshd[29476]: Failed password for invalid user apache from 76.76.97.242 port 33804 ssh2
Mar 14 15:50:16 zelda sshd[29478]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:16 zelda sshd[29478]: Invalid user pgsql from 76.76.97.242
Mar 14 15:50:16 zelda sshd[29478]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:16 zelda sshd[29478]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:18 zelda sshd[29478]: Failed password for invalid user pgsql from 76.76.97.242 port 34113 ssh2
Mar 14 15:50:19 zelda sshd[29482]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:19 zelda sshd[29482]: Invalid user mysql from 76.76.97.242
Mar 14 15:50:19 zelda sshd[29482]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:19 zelda sshd[29482]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:21 zelda sshd[29482]: Failed password for invalid user mysql from 76.76.97.242 port 34413 ssh2
Mar 14 15:50:22 zelda sshd[29484]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:22 zelda sshd[29484]: Invalid user info from 76.76.97.242
Mar 14 15:50:22 zelda sshd[29484]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:22 zelda sshd[29484]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:24 zelda sshd[29484]: Failed password for invalid user info from 76.76.97.242 port 34763 ssh2
Mar 14 15:50:25 zelda sshd[29486]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:25 zelda sshd[29486]: Invalid user tony from 76.76.97.242
Mar 14 15:50:25 zelda sshd[29486]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:25 zelda sshd[29486]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:27 zelda sshd[29486]: Failed password for invalid user tony from 76.76.97.242 port 35079 ssh2
Mar 14 15:50:31 zelda sshd[29489]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:31 zelda sshd[29489]: Invalid user core from 76.76.97.242
Mar 14 15:50:31 zelda sshd[29489]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:31 zelda sshd[29489]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:33 zelda sshd[29489]: Failed password for invalid user core from 76.76.97.242 port 35405 ssh2
Mar 14 15:50:34 zelda sshd[29491]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:34 zelda sshd[29491]: Invalid user newsletter from 76.76.97.242
Mar 14 15:50:34 zelda sshd[29491]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:34 zelda sshd[29491]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:36 zelda sshd[29491]: Failed password for invalid user newsletter from 76.76.97.242 port 36086 ssh2
Mar 14 15:50:37 zelda sshd[29493]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:37 zelda sshd[29493]: Invalid user named from 76.76.97.242
Mar 14 15:50:37 zelda sshd[29493]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:37 zelda sshd[29493]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:39 zelda sshd[29493]: Failed password for invalid user named from 76.76.97.242 port 36414 ssh2
Mar 14 15:50:40 zelda sshd[29495]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:40 zelda sshd[29495]: Invalid user visitor from 76.76.97.242
Mar 14 15:50:40 zelda sshd[29495]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:40 zelda sshd[29495]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:42 zelda sshd[29495]: Failed password for invalid user visitor from 76.76.97.242 port 36724 ssh2
Mar 14 15:50:43 zelda sshd[29497]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:43 zelda sshd[29497]: Invalid user ftpuser from 76.76.97.242
Mar 14 15:50:43 zelda sshd[29497]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:43 zelda sshd[29497]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:45 zelda sshd[29497]: Failed password for invalid user ftpuser from 76.76.97.242 port 54470 ssh2
Mar 14 15:50:46 zelda sshd[29499]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:46 zelda sshd[29499]: Invalid user username from 76.76.97.242
Mar 14 15:50:46 zelda sshd[29499]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:46 zelda sshd[29499]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:48 zelda sshd[29499]: Failed password for invalid user username from 76.76.97.242 port 54829 ssh2
Mar 14 15:50:49 zelda sshd[29501]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:49 zelda sshd[29501]: Invalid user administrator from 76.76.97.242
Mar 14 15:50:49 zelda sshd[29501]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:49 zelda sshd[29501]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:51 zelda sshd[29501]: Failed password for invalid user administrator from 76.76.97.242 port 55102 ssh2
Mar 14 15:50:52 zelda sshd[29503]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:52 zelda sshd[29503]: Invalid user library from 76.76.97.242
Mar 14 15:50:52 zelda sshd[29503]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:52 zelda sshd[29503]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:54 zelda sshd[29503]: Failed password for invalid user library from 76.76.97.242 port 55415 ssh2
Mar 14 15:50:55 zelda sshd[29505]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:55 zelda sshd[29505]: Invalid user test from 76.76.97.242
Mar 14 15:50:55 zelda sshd[29505]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:50:55 zelda sshd[29505]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:50:58 zelda sshd[29505]: Failed password for invalid user test from 76.76.97.242 port 55743 ssh2
Mar 14 15:50:59 zelda sshd[29507]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:50:59 zelda sshd[29507]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:01 zelda sshd[29507]: Failed password for root from 76.76.97.242 port 56119 ssh2
Mar 14 15:51:02 zelda sshd[29510]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:02 zelda sshd[29510]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:04 zelda sshd[29510]: Failed password for root from 76.76.97.242 port 56428 ssh2
Mar 14 15:51:05 zelda sshd[29552]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:05 zelda sshd[29552]: Invalid user admin from 76.76.97.242
Mar 14 15:51:05 zelda sshd[29552]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:05 zelda sshd[29552]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:07 zelda sshd[29552]: Failed password for invalid user admin from 76.76.97.242 port 56743 ssh2
Mar 14 15:51:07 zelda sshd[29561]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:07 zelda sshd[29561]: Invalid user guest from 76.76.97.242
Mar 14 15:51:07 zelda sshd[29561]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:07 zelda sshd[29561]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:10 zelda sshd[29561]: Failed password for invalid user guest from 76.76.97.242 port 57049 ssh2
Mar 14 15:51:11 zelda sshd[29624]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:11 zelda sshd[29624]: Invalid user master from 76.76.97.242
Mar 14 15:51:11 zelda sshd[29624]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:11 zelda sshd[29624]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:13 zelda sshd[29624]: Failed password for invalid user master from 76.76.97.242 port 57354 ssh2
Mar 14 15:51:14 zelda sshd[29692]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:14 zelda sshd[29692]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:16 zelda sshd[29692]: Failed password for root from 76.76.97.242 port 57665 ssh2
Mar 14 15:51:17 zelda sshd[29698]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:17 zelda sshd[29698]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:19 zelda sshd[29698]: Failed password for root from 76.76.97.242 port 57978 ssh2
Mar 14 15:51:20 zelda sshd[29704]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:20 zelda sshd[29704]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:22 zelda sshd[29704]: Failed password for root from 76.76.97.242 port 58303 ssh2
Mar 14 15:51:22 zelda sshd[29710]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:23 zelda sshd[29710]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:25 zelda sshd[29710]: Failed password for root from 76.76.97.242 port 58592 ssh2
Mar 14 15:51:25 zelda sshd[29716]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:26 zelda sshd[29716]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:28 zelda sshd[29716]: Failed password for root from 76.76.97.242 port 58934 ssh2
Mar 14 15:51:29 zelda sshd[29722]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:29 zelda sshd[29722]: Invalid user admin from 76.76.97.242
Mar 14 15:51:29 zelda sshd[29722]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:29 zelda sshd[29722]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:31 zelda sshd[29722]: Failed password for invalid user admin from 76.76.97.242 port 59277 ssh2
Mar 14 15:51:36 zelda sshd[29736]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:36 zelda sshd[29736]: Invalid user admin from 76.76.97.242
Mar 14 15:51:36 zelda sshd[29736]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:36 zelda sshd[29736]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:38 zelda sshd[29736]: Failed password for invalid user admin from 76.76.97.242 port 59624 ssh2
Mar 14 15:51:39 zelda sshd[29751]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:39 zelda sshd[29751]: Invalid user admin from 76.76.97.242
Mar 14 15:51:39 zelda sshd[29751]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:39 zelda sshd[29751]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:40 zelda sshd[29751]: Failed password for invalid user admin from 76.76.97.242 port 60294 ssh2
Mar 14 15:51:44 zelda sshd[29763]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:45 zelda sshd[29763]: Invalid user admin from 76.76.97.242
Mar 14 15:51:45 zelda sshd[29763]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:45 zelda sshd[29763]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:46 zelda sshd[29763]: Failed password for invalid user admin from 76.76.97.242 port 60571 ssh2
Mar 14 15:51:47 zelda sshd[29766]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:47 zelda sshd[29766]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:49 zelda sshd[29766]: Failed password for root from 76.76.97.242 port 33017 ssh2
Mar 14 15:51:50 zelda sshd[29768]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:50 zelda sshd[29768]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:51:51 zelda sshd[29768]: Failed password for root from 76.76.97.242 port 33314 ssh2
Mar 14 15:51:52 zelda sshd[29770]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:52 zelda sshd[29770]: Invalid user test from 76.76.97.242
Mar 14 15:51:52 zelda sshd[29770]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:52 zelda sshd[29770]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:55 zelda sshd[29770]: Failed password for invalid user test from 76.76.97.242 port 33548 ssh2
Mar 14 15:51:55 zelda sshd[29772]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:55 zelda sshd[29772]: Invalid user test from 76.76.97.242
Mar 14 15:51:55 zelda sshd[29772]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:55 zelda sshd[29772]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:51:58 zelda sshd[29772]: Failed password for invalid user test from 76.76.97.242 port 33920 ssh2
Mar 14 15:51:58 zelda sshd[29774]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:51:58 zelda sshd[29774]: Invalid user webmaster from 76.76.97.242
Mar 14 15:51:58 zelda sshd[29774]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:51:58 zelda sshd[29774]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:01 zelda sshd[29774]: Failed password for invalid user webmaster from 76.76.97.242 port 34246 ssh2
Mar 14 15:52:02 zelda sshd[29776]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:02 zelda sshd[29776]: Invalid user username from 76.76.97.242
Mar 14 15:52:02 zelda sshd[29776]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:02 zelda sshd[29776]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:03 zelda sshd[29776]: Failed password for invalid user username from 76.76.97.242 port 34557 ssh2
Mar 14 15:52:04 zelda sshd[29778]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:04 zelda sshd[29778]: Invalid user user from 76.76.97.242
Mar 14 15:52:04 zelda sshd[29778]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:04 zelda sshd[29778]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:06 zelda sshd[29778]: Failed password for invalid user user from 76.76.97.242 port 34786 ssh2
Mar 14 15:52:07 zelda sshd[29780]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:07 zelda sshd[29780]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:52:09 zelda sshd[29780]: Failed password for root from 76.76.97.242 port 35111 ssh2
Mar 14 15:52:10 zelda sshd[29782]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:10 zelda sshd[29782]: Invalid user admin from 76.76.97.242
Mar 14 15:52:10 zelda sshd[29782]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:10 zelda sshd[29782]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:12 zelda sshd[29782]: Failed password for invalid user admin from 76.76.97.242 port 35509 ssh2
Mar 14 15:52:13 zelda sshd[29784]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:13 zelda sshd[29784]: Invalid user test from 76.76.97.242
Mar 14 15:52:13 zelda sshd[29784]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:13 zelda sshd[29784]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:15 zelda sshd[29784]: Failed password for invalid user test from 76.76.97.242 port 35827 ssh2
Mar 14 15:52:16 zelda sshd[29786]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:16 zelda sshd[29786]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:52:18 zelda sshd[29786]: Failed password for root from 76.76.97.242 port 36121 ssh2
Mar 14 15:52:19 zelda sshd[29788]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:19 zelda sshd[29788]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:52:21 zelda sshd[29788]: Failed password for root from 76.76.97.242 port 36435 ssh2
Mar 14 15:52:22 zelda sshd[29790]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:22 zelda sshd[29790]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:52:25 zelda sshd[29790]: Failed password for root from 76.76.97.242 port 36793 ssh2
Mar 14 15:52:26 zelda sshd[29792]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:26 zelda sshd[29792]: Invalid user danny from 76.76.97.242
Mar 14 15:52:26 zelda sshd[29792]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:26 zelda sshd[29792]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:27 zelda sshd[29792]: Failed password for invalid user danny from 76.76.97.242 port 37152 ssh2
Mar 14 15:52:28 zelda sshd[29794]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:28 zelda sshd[29794]: Invalid user alex from 76.76.97.242
Mar 14 15:52:28 zelda sshd[29794]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:28 zelda sshd[29794]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:30 zelda sshd[29794]: Failed password for invalid user alex from 76.76.97.242 port 37411 ssh2
Mar 14 15:52:31 zelda sshd[29796]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:31 zelda sshd[29796]: Invalid user brett from 76.76.97.242
Mar 14 15:52:31 zelda sshd[29796]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:31 zelda sshd[29796]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:34 zelda sshd[29796]: Failed password for invalid user brett from 76.76.97.242 port 37761 ssh2
Mar 14 15:52:34 zelda sshd[29798]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:34 zelda sshd[29798]: Invalid user mike from 76.76.97.242
Mar 14 15:52:34 zelda sshd[29798]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:34 zelda sshd[29798]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:36 zelda sshd[29798]: Failed password for invalid user mike from 76.76.97.242 port 38124 ssh2
Mar 14 15:52:37 zelda sshd[29800]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:37 zelda sshd[29800]: Invalid user alan from 76.76.97.242
Mar 14 15:52:37 zelda sshd[29800]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:37 zelda sshd[29800]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:39 zelda sshd[29800]: Failed password for invalid user alan from 76.76.97.242 port 38423 ssh2
Mar 14 15:52:43 zelda sshd[29802]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:43 zelda sshd[29802]: Invalid user data from 76.76.97.242
Mar 14 15:52:43 zelda sshd[29802]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:43 zelda sshd[29802]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:45 zelda sshd[29802]: Failed password for invalid user data from 76.76.97.242 port 38696 ssh2
Mar 14 15:52:46 zelda sshd[29804]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:46 zelda sshd[29804]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=www-data
Mar 14 15:52:48 zelda sshd[29804]: Failed password for www-data from 76.76.97.242 port 39387 ssh2
Mar 14 15:52:49 zelda sshd[29806]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:49 zelda sshd[29806]: Invalid user http from 76.76.97.242
Mar 14 15:52:49 zelda sshd[29806]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:49 zelda sshd[29806]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:51 zelda sshd[29806]: Failed password for invalid user http from 76.76.97.242 port 39699 ssh2
Mar 14 15:52:51 zelda sshd[29808]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:51 zelda sshd[29808]: Invalid user httpd from 76.76.97.242
Mar 14 15:52:51 zelda sshd[29808]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:51 zelda sshd[29808]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:53 zelda sshd[29808]: Failed password for invalid user httpd from 76.76.97.242 port 39966 ssh2
Mar 14 15:52:54 zelda sshd[29810]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:54 zelda sshd[29810]: Invalid user pop from 76.76.97.242
Mar 14 15:52:54 zelda sshd[29810]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:52:54 zelda sshd[29810]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:52:56 zelda sshd[29810]: Failed password for invalid user pop from 76.76.97.242 port 40284 ssh2
Mar 14 15:52:57 zelda sshd[29812]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:52:57 zelda sshd[29812]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=nobody
Mar 14 15:52:59 zelda sshd[29812]: Failed password for nobody from 76.76.97.242 port 40608 ssh2
Mar 14 15:53:00 zelda sshd[29814]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:00 zelda sshd[29814]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=root
Mar 14 15:53:02 zelda sshd[29814]: Failed password for root from 76.76.97.242 port 40864 ssh2
Mar 14 15:53:03 zelda sshd[29816]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:03 zelda sshd[29816]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=backup
Mar 14 15:53:05 zelda sshd[29816]: Failed password for backup from 76.76.97.242 port 41173 ssh2
Mar 14 15:53:06 zelda sshd[29818]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:06 zelda sshd[29818]: Invalid user info from 76.76.97.242
Mar 14 15:53:06 zelda sshd[29818]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:06 zelda sshd[29818]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:08 zelda sshd[29818]: Failed password for invalid user info from 76.76.97.242 port 41515 ssh2
Mar 14 15:53:09 zelda sshd[29820]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:09 zelda sshd[29820]: Invalid user shop from 76.76.97.242
Mar 14 15:53:09 zelda sshd[29820]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:09 zelda sshd[29820]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:11 zelda sshd[29820]: Failed password for invalid user shop from 76.76.97.242 port 41859 ssh2
Mar 14 15:53:12 zelda sshd[29822]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:12 zelda sshd[29822]: Invalid user sales from 76.76.97.242
Mar 14 15:53:12 zelda sshd[29822]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:12 zelda sshd[29822]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:13 zelda sshd[29822]: Failed password for invalid user sales from 76.76.97.242 port 42136 ssh2
Mar 14 15:53:14 zelda sshd[29824]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:14 zelda sshd[29824]: Invalid user web from 76.76.97.242
Mar 14 15:53:14 zelda sshd[29824]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:14 zelda sshd[29824]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:16 zelda sshd[29824]: Failed password for invalid user web from 76.76.97.242 port 42397 ssh2
Mar 14 15:53:17 zelda sshd[29826]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:17 zelda sshd[29826]: Invalid user www from 76.76.97.242
Mar 14 15:53:17 zelda sshd[29826]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:17 zelda sshd[29826]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:19 zelda sshd[29826]: Failed password for invalid user www from 76.76.97.242 port 42670 ssh2
Mar 14 15:53:20 zelda sshd[29828]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:20 zelda sshd[29828]: Invalid user wwwrun from 76.76.97.242
Mar 14 15:53:20 zelda sshd[29828]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:20 zelda sshd[29828]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:21 zelda sshd[29828]: Failed password for invalid user wwwrun from 76.76.97.242 port 42977 ssh2
Mar 14 15:53:22 zelda sshd[29830]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:22 zelda sshd[29830]: Invalid user adam from 76.76.97.242
Mar 14 15:53:22 zelda sshd[29830]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:22 zelda sshd[29830]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:24 zelda sshd[29830]: Failed password for invalid user adam from 76.76.97.242 port 43230 ssh2
Mar 14 15:53:24 zelda sshd[29832]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:24 zelda sshd[29832]: Invalid user stephen from 76.76.97.242
Mar 14 15:53:24 zelda sshd[29832]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:24 zelda sshd[29832]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:26 zelda sshd[29832]: Failed password for invalid user stephen from 76.76.97.242 port 43469 ssh2
Mar 14 15:53:32 zelda sshd[29834]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:32 zelda sshd[29834]: Invalid user richard from 76.76.97.242
Mar 14 15:53:32 zelda sshd[29834]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:32 zelda sshd[29834]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:34 zelda sshd[29834]: Failed password for invalid user richard from 76.76.97.242 port 43732 ssh2
Mar 14 15:53:34 zelda sshd[29844]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:34 zelda sshd[29844]: Invalid user george from 76.76.97.242
Mar 14 15:53:34 zelda sshd[29844]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:34 zelda sshd[29844]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:36 zelda sshd[29844]: Failed password for invalid user george from 76.76.97.242 port 44508 ssh2
Mar 14 15:53:37 zelda sshd[29847]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:37 zelda sshd[29847]: Invalid user john from 76.76.97.242
Mar 14 15:53:37 zelda sshd[29847]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:37 zelda sshd[29847]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:39 zelda sshd[29847]: Failed password for invalid user john from 76.76.97.242 port 44774 ssh2
Mar 14 15:53:40 zelda sshd[29849]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:40 zelda sshd[29849]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=news
Mar 14 15:53:42 zelda sshd[29849]: Failed password for news from 76.76.97.242 port 45047 ssh2
Mar 14 15:53:43 zelda sshd[29851]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:43 zelda sshd[29851]: Invalid user angel from 76.76.97.242
Mar 14 15:53:43 zelda sshd[29851]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:43 zelda sshd[29851]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:45 zelda sshd[29851]: Failed password for invalid user angel from 76.76.97.242 port 45412 ssh2
Mar 14 15:53:45 zelda sshd[29853]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:45 zelda sshd[29853]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=games
Mar 14 15:53:47 zelda sshd[29853]: Failed password for games from 76.76.97.242 port 45686 ssh2
Mar 14 15:53:53 zelda sshd[29855]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:53 zelda sshd[29855]: Invalid user pgsql from 76.76.97.242
Mar 14 15:53:53 zelda sshd[29855]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:53 zelda sshd[29855]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:54 zelda sshd[29855]: Failed password for invalid user pgsql from 76.76.97.242 port 45915 ssh2
Mar 14 15:53:55 zelda sshd[29861]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:55 zelda sshd[29861]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=mail
Mar 14 15:53:57 zelda sshd[29861]: Failed password for mail from 76.76.97.242 port 46685 ssh2
Mar 14 15:53:58 zelda sshd[29863]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:53:58 zelda sshd[29863]: Invalid user adm from 76.76.97.242
Mar 14 15:53:58 zelda sshd[29863]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:53:58 zelda sshd[29863]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:53:58 zelda sshd[27926]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 15:53:58 zelda sshd[27916]: pam_unix(sshd:session): session closed for user trevor
Mar 14 15:53:58 zelda sshd[27916]: Mount of private directory return code [0]
Mar 14 15:54:00 zelda sshd[29863]: Failed password for invalid user adm from 76.76.97.242 port 46973 ssh2
Mar 14 15:54:01 zelda sshd[29874]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:01 zelda sshd[29874]: Invalid user ident from 76.76.97.242
Mar 14 15:54:01 zelda sshd[29874]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:01 zelda sshd[29874]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:03 zelda sshd[29874]: Failed password for invalid user ident from 76.76.97.242 port 47270 ssh2
Mar 14 15:54:04 zelda sshd[29876]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:04 zelda sshd[29876]: Invalid user webpop from 76.76.97.242
Mar 14 15:54:04 zelda sshd[29876]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:04 zelda sshd[29876]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:05 zelda sshd[29876]: Failed password for invalid user webpop from 76.76.97.242 port 47616 ssh2
Mar 14 15:54:06 zelda sshd[29878]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:06 zelda sshd[29878]: Invalid user susan from 76.76.97.242
Mar 14 15:54:06 zelda sshd[29878]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:06 zelda sshd[29878]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:08 zelda sshd[29878]: Failed password for invalid user susan from 76.76.97.242 port 47884 ssh2
Mar 14 15:54:09 zelda sshd[29880]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:09 zelda sshd[29880]: Invalid user sunny from 76.76.97.242
Mar 14 15:54:09 zelda sshd[29880]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:09 zelda sshd[29880]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:11 zelda sshd[29880]: Failed password for invalid user sunny from 76.76.97.242 port 48217 ssh2
Mar 14 15:54:11 zelda sshd[29882]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:11 zelda sshd[29882]: Invalid user steven from 76.76.97.242
Mar 14 15:54:11 zelda sshd[29882]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:11 zelda sshd[29882]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:13 zelda sshd[29882]: Failed password for invalid user steven from 76.76.97.242 port 48450 ssh2
Mar 14 15:54:14 zelda sshd[29884]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:14 zelda sshd[29884]: Invalid user ssh from 76.76.97.242
Mar 14 15:54:14 zelda sshd[29884]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:14 zelda sshd[29884]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:16 zelda sshd[29884]: Failed password for invalid user ssh from 76.76.97.242 port 48726 ssh2
Mar 14 15:54:17 zelda sshd[29886]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:17 zelda sshd[29886]: Invalid user search from 76.76.97.242
Mar 14 15:54:17 zelda sshd[29886]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:17 zelda sshd[29886]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:19 zelda sshd[29886]: Failed password for invalid user search from 76.76.97.242 port 49051 ssh2
Mar 14 15:54:19 zelda sshd[29888]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:19 zelda sshd[29888]: Invalid user sara from 76.76.97.242
Mar 14 15:54:20 zelda sshd[29888]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:20 zelda sshd[29888]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:22 zelda sshd[29888]: Failed password for invalid user sara from 76.76.97.242 port 49383 ssh2
Mar 14 15:54:22 zelda sshd[29890]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:22 zelda sshd[29890]: Invalid user robert from 76.76.97.242
Mar 14 15:54:22 zelda sshd[29890]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:22 zelda sshd[29890]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:24 zelda sshd[29890]: Failed password for invalid user robert from 76.76.97.242 port 49673 ssh2
Mar 14 15:54:25 zelda sshd[29892]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:25 zelda sshd[29892]: Invalid user richard from 76.76.97.242
Mar 14 15:54:25 zelda sshd[29892]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:25 zelda sshd[29892]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:27 zelda sshd[29892]: Failed password for invalid user richard from 76.76.97.242 port 49984 ssh2
Mar 14 15:54:28 zelda sshd[29894]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:28 zelda sshd[29894]: Invalid user party from 76.76.97.242
Mar 14 15:54:28 zelda sshd[29894]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:28 zelda sshd[29894]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:29 zelda sshd[29894]: Failed password for invalid user party from 76.76.97.242 port 50268 ssh2
Mar 14 15:54:30 zelda sshd[29896]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:30 zelda sshd[29896]: Invalid user amanda from 76.76.97.242
Mar 14 15:54:30 zelda sshd[29896]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:30 zelda sshd[29896]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:32 zelda sshd[29896]: Failed password for invalid user amanda from 76.76.97.242 port 50524 ssh2
Mar 14 15:54:33 zelda sshd[29898]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:33 zelda sshd[29898]: Invalid user rpm from 76.76.97.242
Mar 14 15:54:33 zelda sshd[29898]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:33 zelda sshd[29898]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:35 zelda sshd[29898]: Failed password for invalid user rpm from 76.76.97.242 port 50834 ssh2
Mar 14 15:54:36 zelda sshd[29900]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:36 zelda sshd[29900]: Invalid user operator from 76.76.97.242
Mar 14 15:54:36 zelda sshd[29900]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:36 zelda sshd[29900]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:38 zelda sshd[29900]: Failed password for invalid user operator from 76.76.97.242 port 51077 ssh2
Mar 14 15:54:39 zelda sshd[29902]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:39 zelda sshd[29902]: Invalid user sgi from 76.76.97.242
Mar 14 15:54:39 zelda sshd[29902]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:39 zelda sshd[29902]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:40 zelda sshd[29902]: Failed password for invalid user sgi from 76.76.97.242 port 51414 ssh2
Mar 14 15:54:41 zelda sshd[29904]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:41 zelda sshd[29904]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=sshd
Mar 14 15:54:43 zelda sshd[29904]: Failed password for sshd from 76.76.97.242 port 51627 ssh2
Mar 14 15:54:44 zelda sshd[29906]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:44 zelda sshd[29906]: Invalid user users from 76.76.97.242
Mar 14 15:54:44 zelda sshd[29906]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:44 zelda sshd[29906]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:45 zelda sshd[29906]: Failed password for invalid user users from 76.76.97.242 port 51909 ssh2
Mar 14 15:54:49 zelda sshd[29908]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:49 zelda sshd[29908]: Invalid user admins from 76.76.97.242
Mar 14 15:54:49 zelda sshd[29908]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:49 zelda sshd[29908]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:52 zelda sshd[29908]: Failed password for invalid user admins from 76.76.97.242 port 52123 ssh2
Mar 14 15:54:52 zelda sshd[29910]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:52 zelda sshd[29910]: Invalid user admins from 76.76.97.242
Mar 14 15:54:52 zelda sshd[29910]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:54:52 zelda sshd[29910]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:54:54 zelda sshd[29910]: Failed password for invalid user admins from 76.76.97.242 port 52749 ssh2
Mar 14 15:54:55 zelda sshd[29912]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:55 zelda sshd[29912]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=bin
Mar 14 15:54:57 zelda sshd[29912]: Failed password for bin from 76.76.97.242 port 53029 ssh2
Mar 14 15:54:58 zelda sshd[29914]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:54:58 zelda sshd[29914]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=daemon
Mar 14 15:54:59 zelda sshd[29914]: Failed password for daemon from 76.76.97.242 port 53289 ssh2
Mar 14 15:55:00 zelda sshd[29916]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:00 zelda sshd[29916]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=lp
Mar 14 15:55:02 zelda sshd[29916]: Failed password for lp from 76.76.97.242 port 53519 ssh2
Mar 14 15:55:03 zelda sshd[29918]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:03 zelda sshd[29918]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=sync
Mar 14 15:55:05 zelda sshd[29918]: Failed password for sync from 76.76.97.242 port 53817 ssh2
Mar 14 15:55:05 zelda sshd[29920]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:05 zelda sshd[29920]: Invalid user shutdown from 76.76.97.242
Mar 14 15:55:05 zelda sshd[29920]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:05 zelda sshd[29920]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:07 zelda sshd[29920]: Failed password for invalid user shutdown from 76.76.97.242 port 54028 ssh2
Mar 14 15:55:08 zelda sshd[29922]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:08 zelda sshd[29922]: Invalid user halt from 76.76.97.242
Mar 14 15:55:08 zelda sshd[29922]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:08 zelda sshd[29922]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:10 zelda sshd[29922]: Failed password for invalid user halt from 76.76.97.242 port 54287 ssh2
Mar 14 15:55:11 zelda sshd[29924]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:11 zelda sshd[29924]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=uucp
Mar 14 15:55:13 zelda sshd[29924]: Failed password for uucp from 76.76.97.242 port 54543 ssh2
Mar 14 15:55:14 zelda sshd[29926]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:14 zelda sshd[29926]: Invalid user smmsp from 76.76.97.242
Mar 14 15:55:14 zelda sshd[29926]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:14 zelda sshd[29926]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:15 zelda sshd[29926]: Failed password for invalid user smmsp from 76.76.97.242 port 54813 ssh2
Mar 14 15:55:16 zelda sshd[29928]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:16 zelda sshd[29928]: Invalid user dean from 76.76.97.242
Mar 14 15:55:16 zelda sshd[29928]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:16 zelda sshd[29928]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:18 zelda sshd[29928]: Failed password for invalid user dean from 76.76.97.242 port 54998 ssh2
Mar 14 15:55:19 zelda sshd[29930]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:19 zelda sshd[29930]: Invalid user unknown from 76.76.97.242
Mar 14 15:55:19 zelda sshd[29930]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:19 zelda sshd[29930]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:21 zelda sshd[29930]: Failed password for invalid user unknown from 76.76.97.242 port 55268 ssh2
Mar 14 15:55:22 zelda sshd[29932]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:22 zelda sshd[29932]: Invalid user securityagent from 76.76.97.242
Mar 14 15:55:22 zelda sshd[29932]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:22 zelda sshd[29932]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:24 zelda sshd[29932]: Failed password for invalid user securityagent from 76.76.97.242 port 55573 ssh2
Mar 14 15:55:25 zelda sshd[29934]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:25 zelda sshd[29934]: Invalid user tokend from 76.76.97.242
Mar 14 15:55:25 zelda sshd[29934]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:25 zelda sshd[29934]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:27 zelda sshd[29934]: Failed password for invalid user tokend from 76.76.97.242 port 55770 ssh2
Mar 14 15:55:28 zelda sshd[29936]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:28 zelda sshd[29936]: Invalid user windowserver from 76.76.97.242
Mar 14 15:55:28 zelda sshd[29936]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:28 zelda sshd[29936]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:30 zelda sshd[29936]: Failed password for invalid user windowserver from 76.76.97.242 port 56068 ssh2
Mar 14 15:55:31 zelda sshd[29938]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:31 zelda sshd[29938]: Invalid user appowner from 76.76.97.242
Mar 14 15:55:31 zelda sshd[29938]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:31 zelda sshd[29938]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:33 zelda sshd[29938]: Failed password for invalid user appowner from 76.76.97.242 port 56337 ssh2
Mar 14 15:55:34 zelda sshd[29940]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:34 zelda sshd[29940]: Invalid user xgridagent from 76.76.97.242
Mar 14 15:55:34 zelda sshd[29940]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:34 zelda sshd[29940]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:36 zelda sshd[29940]: Failed password for invalid user xgridagent from 76.76.97.242 port 56624 ssh2
Mar 14 15:55:37 zelda sshd[29942]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:37 zelda sshd[29942]: Invalid user agent from 76.76.97.242
Mar 14 15:55:37 zelda sshd[29942]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:37 zelda sshd[29942]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:39 zelda sshd[29942]: Failed password for invalid user agent from 76.76.97.242 port 56856 ssh2
Mar 14 15:55:40 zelda sshd[29944]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:40 zelda sshd[29944]: Invalid user xgridcontroller from 76.76.97.242
Mar 14 15:55:40 zelda sshd[29944]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:40 zelda sshd[29944]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:41 zelda sshd[29944]: Failed password for invalid user xgridcontroller from 76.76.97.242 port 57145 ssh2
Mar 14 15:55:42 zelda sshd[29946]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:42 zelda sshd[29946]: Invalid user jabber from 76.76.97.242
Mar 14 15:55:42 zelda sshd[29946]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:42 zelda sshd[29946]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:44 zelda sshd[29946]: Failed password for invalid user jabber from 76.76.97.242 port 49904 ssh2
Mar 14 15:55:45 zelda sshd[29948]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:45 zelda sshd[29948]: Invalid user amavisd from 76.76.97.242
Mar 14 15:55:45 zelda sshd[29948]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:45 zelda sshd[29948]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:47 zelda sshd[29948]: Failed password for invalid user amavisd from 76.76.97.242 port 50191 ssh2
Mar 14 15:55:47 zelda sshd[29950]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:47 zelda sshd[29950]: Invalid user clamav from 76.76.97.242
Mar 14 15:55:47 zelda sshd[29950]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:47 zelda sshd[29950]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:50 zelda sshd[29950]: Failed password for invalid user clamav from 76.76.97.242 port 50385 ssh2
Mar 14 15:55:50 zelda sshd[29952]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:50 zelda sshd[29952]: Invalid user appserver from 76.76.97.242
Mar 14 15:55:50 zelda sshd[29952]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:50 zelda sshd[29952]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:52 zelda sshd[29952]: Failed password for invalid user appserver from 76.76.97.242 port 50657 ssh2
Mar 14 15:55:52 zelda sshd[29954]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:52 zelda sshd[29954]: Invalid user mailman from 76.76.97.242
Mar 14 15:55:52 zelda sshd[29954]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:52 zelda sshd[29954]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:54 zelda sshd[29954]: Failed password for invalid user mailman from 76.76.97.242 port 50826 ssh2
Mar 14 15:55:55 zelda sshd[29956]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:55 zelda sshd[29956]: Invalid user cyrusimap from 76.76.97.242
Mar 14 15:55:55 zelda sshd[29956]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:55 zelda sshd[29956]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:55:57 zelda sshd[29956]: Failed password for invalid user cyrusimap from 76.76.97.242 port 51052 ssh2
Mar 14 15:55:58 zelda sshd[29958]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:55:58 zelda sshd[29958]: Invalid user qtss from 76.76.97.242
Mar 14 15:55:58 zelda sshd[29958]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:55:58 zelda sshd[29958]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:00 zelda sshd[29958]: Failed password for invalid user qtss from 76.76.97.242 port 51313 ssh2
Mar 14 15:56:01 zelda sshd[29960]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:01 zelda sshd[29960]: Invalid user eppc from 76.76.97.242
Mar 14 15:56:01 zelda sshd[29960]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:01 zelda sshd[29960]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:04 zelda sshd[29960]: Failed password for invalid user eppc from 76.76.97.242 port 51549 ssh2
Mar 14 15:56:04 zelda sshd[29962]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:04 zelda sshd[29962]: Invalid user telnetd from 76.76.97.242
Mar 14 15:56:04 zelda sshd[29962]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:04 zelda sshd[29962]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:06 zelda sshd[29962]: Failed password for invalid user telnetd from 76.76.97.242 port 51853 ssh2
Mar 14 15:56:07 zelda sshd[29964]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:07 zelda sshd[29964]: Invalid user identd from 76.76.97.242
Mar 14 15:56:07 zelda sshd[29964]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:07 zelda sshd[29964]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:09 zelda sshd[29964]: Failed password for invalid user identd from 76.76.97.242 port 52095 ssh2
Mar 14 15:56:10 zelda sshd[29966]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:10 zelda sshd[29966]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=gnats
Mar 14 15:56:12 zelda sshd[29966]: Failed password for gnats from 76.76.97.242 port 52341 ssh2
Mar 14 15:56:13 zelda sshd[29968]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:13 zelda sshd[29968]: Invalid user jeff from 76.76.97.242
Mar 14 15:56:13 zelda sshd[29968]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:13 zelda sshd[29968]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:15 zelda sshd[29968]: Failed password for invalid user jeff from 76.76.97.242 port 52593 ssh2
Mar 14 15:56:16 zelda sshd[29970]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:16 zelda sshd[29970]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=irc
Mar 14 15:56:18 zelda sshd[29970]: Failed password for irc from 76.76.97.242 port 52884 ssh2
Mar 14 15:56:19 zelda sshd[29972]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:19 zelda sshd[29972]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=list
Mar 14 15:56:21 zelda sshd[29972]: Failed password for list from 76.76.97.242 port 53136 ssh2
Mar 14 15:56:22 zelda sshd[29974]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:22 zelda sshd[29974]: Invalid user eleve from 76.76.97.242
Mar 14 15:56:22 zelda sshd[29974]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:22 zelda sshd[29974]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:24 zelda sshd[29974]: Failed password for invalid user eleve from 76.76.97.242 port 53384 ssh2
Mar 14 15:56:25 zelda sshd[29976]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:25 zelda sshd[29976]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=proxy
Mar 14 15:56:27 zelda sshd[29976]: Failed password for proxy from 76.76.97.242 port 53607 ssh2
Mar 14 15:56:28 zelda sshd[29978]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:28 zelda sshd[29978]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242  user=sys
Mar 14 15:56:30 zelda sshd[29978]: Failed password for sys from 76.76.97.242 port 53923 ssh2
Mar 14 15:56:31 zelda sshd[29980]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:31 zelda sshd[29980]: Invalid user zzz from 76.76.97.242
Mar 14 15:56:31 zelda sshd[29980]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:31 zelda sshd[29980]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:33 zelda sshd[29980]: Failed password for invalid user zzz from 76.76.97.242 port 54149 ssh2
Mar 14 15:56:34 zelda sshd[29982]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:34 zelda sshd[29982]: Invalid user frank from 76.76.97.242
Mar 14 15:56:34 zelda sshd[29982]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:34 zelda sshd[29982]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:36 zelda sshd[29982]: Failed password for invalid user frank from 76.76.97.242 port 54416 ssh2
Mar 14 15:56:37 zelda sshd[29984]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:37 zelda sshd[29984]: Invalid user dan from 76.76.97.242
Mar 14 15:56:37 zelda sshd[29984]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:37 zelda sshd[29984]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:39 zelda sshd[29984]: Failed password for invalid user dan from 76.76.97.242 port 54651 ssh2
Mar 14 15:56:40 zelda sshd[29986]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:40 zelda sshd[29986]: Invalid user james from 76.76.97.242
Mar 14 15:56:40 zelda sshd[29986]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:40 zelda sshd[29986]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:42 zelda sshd[29986]: Failed password for invalid user james from 76.76.97.242 port 54965 ssh2
Mar 14 15:56:48 zelda sshd[29988]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:48 zelda sshd[29988]: Invalid user snort from 76.76.97.242
Mar 14 15:56:48 zelda sshd[29988]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:48 zelda sshd[29988]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:50 zelda sshd[29988]: Failed password for invalid user snort from 76.76.97.242 port 55219 ssh2
Mar 14 15:56:51 zelda sshd[29990]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:51 zelda sshd[29990]: Invalid user radiomail from 76.76.97.242
Mar 14 15:56:51 zelda sshd[29990]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:51 zelda sshd[29990]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:53 zelda sshd[29990]: Failed password for invalid user radiomail from 76.76.97.242 port 56020 ssh2
Mar 14 15:56:54 zelda sshd[29992]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:54 zelda sshd[29992]: Invalid user harrypotter from 76.76.97.242
Mar 14 15:56:54 zelda sshd[29992]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:54 zelda sshd[29992]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:56 zelda sshd[29992]: Failed password for invalid user harrypotter from 76.76.97.242 port 56242 ssh2
Mar 14 15:56:57 zelda sshd[29994]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:57 zelda sshd[29994]: Invalid user divine from 76.76.97.242
Mar 14 15:56:57 zelda sshd[29994]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:57 zelda sshd[29994]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:56:58 zelda sshd[29994]: Failed password for invalid user divine from 76.76.97.242 port 56503 ssh2
Mar 14 15:56:59 zelda sshd[29996]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:56:59 zelda sshd[29996]: Invalid user popa3d from 76.76.97.242
Mar 14 15:56:59 zelda sshd[29996]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:56:59 zelda sshd[29996]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:02 zelda sshd[29996]: Failed password for invalid user popa3d from 76.76.97.242 port 56746 ssh2
Mar 14 15:57:02 zelda sshd[29998]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:02 zelda sshd[29998]: Invalid user aptproxy from 76.76.97.242
Mar 14 15:57:02 zelda sshd[29998]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:02 zelda sshd[29998]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:05 zelda sshd[29998]: Failed password for invalid user aptproxy from 76.76.97.242 port 57036 ssh2
Mar 14 15:57:06 zelda sshd[30000]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:06 zelda sshd[30000]: Invalid user desktop from 76.76.97.242
Mar 14 15:57:06 zelda sshd[30000]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:06 zelda sshd[30000]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:08 zelda sshd[30000]: Failed password for invalid user desktop from 76.76.97.242 port 57371 ssh2
Mar 14 15:57:09 zelda sshd[30002]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:09 zelda sshd[30002]: Invalid user workshop from 76.76.97.242
Mar 14 15:57:09 zelda sshd[30002]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:09 zelda sshd[30002]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:11 zelda sshd[30002]: Failed password for invalid user workshop from 76.76.97.242 port 57615 ssh2
Mar 14 15:57:12 zelda sshd[30004]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:12 zelda sshd[30004]: Invalid user mailnull from 76.76.97.242
Mar 14 15:57:12 zelda sshd[30004]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:12 zelda sshd[30004]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:14 zelda sshd[30004]: Failed password for invalid user mailnull from 76.76.97.242 port 57885 ssh2
Mar 14 15:57:18 zelda sshd[30006]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:18 zelda sshd[30006]: Invalid user nfsnobody from 76.76.97.242
Mar 14 15:57:18 zelda sshd[30006]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:18 zelda sshd[30006]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:20 zelda sshd[30006]: Failed password for invalid user nfsnobody from 76.76.97.242 port 58172 ssh2
Mar 14 15:57:21 zelda sshd[30008]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:21 zelda sshd[30008]: Invalid user rpcuser from 76.76.97.242
Mar 14 15:57:21 zelda sshd[30008]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:21 zelda sshd[30008]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:22 zelda sshd[30008]: Failed password for invalid user rpcuser from 76.76.97.242 port 58735 ssh2
Mar 14 15:57:23 zelda sshd[30010]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:23 zelda sshd[30010]: Invalid user rpc from 76.76.97.242
Mar 14 15:57:23 zelda sshd[30010]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:23 zelda sshd[30010]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:26 zelda sshd[30010]: Failed password for invalid user rpc from 76.76.97.242 port 58964 ssh2
Mar 14 15:57:26 zelda sshd[30012]: Address 76.76.97.242 maps to reverse-mtl-76-76-97-242.gogax.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Mar 14 15:57:26 zelda sshd[30012]: Invalid user gopher from 76.76.97.242
Mar 14 15:57:26 zelda sshd[30012]: pam_unix(sshd:auth): check pass; user unknown
Mar 14 15:57:26 zelda sshd[30012]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=76.76.97.242 
Mar 14 15:57:29 zelda sshd[30012]: Failed password for invalid user gopher from 76.76.97.242 port 59254 ssh2
Mar 14 16:02:48 zelda sshd[30101]: pam_sm_authenticate: Called 
Mar 14 16:02:48 zelda sshd[30101]: pam_sm_authenticate: username = [trevor] 
Mar 14 16:02:48 zelda sshd[30101]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 16:02:52 zelda sshd[30103]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:02:52 zelda sshd[30103]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 16:02:52 zelda sshd[30103]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 16:02:53 zelda sshd[30103]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:02:54 zelda sshd[30103]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 16:02:54 zelda sshd[30103]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 16:02:54 zelda sshd[30103]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 16:02:54 zelda sshd[30101]: Accepted password for trevor from 192.168.0.101 port 1353 ssh2
Mar 14 16:02:54 zelda sshd[30101]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 16:02:54 zelda sshd[30101]: Mount of private directory return code [0]
Mar 14 16:03:33 zelda sshd[30111]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 16:03:33 zelda sshd[30101]: pam_unix(sshd:session): session closed for user trevor
Mar 14 16:03:33 zelda sshd[30101]: Mount of private directory return code [0]
Mar 14 16:05:32 zelda sshd[30141]: pam_sm_authenticate: Called 
Mar 14 16:05:32 zelda sshd[30141]: pam_sm_authenticate: username = [trevor] 
Mar 14 16:05:32 zelda sshd[30141]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 16:05:36 zelda sshd[30143]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:05:36 zelda sshd[30143]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 16:05:36 zelda sshd[30143]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 16:05:38 zelda sshd[30143]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:05:38 zelda sshd[30143]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 16:05:38 zelda sshd[30143]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 16:05:38 zelda sshd[30143]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 16:05:38 zelda sshd[30141]: Accepted password for trevor from 192.168.0.101 port 1377 ssh2
Mar 14 16:05:38 zelda sshd[30141]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 16:05:38 zelda sshd[30141]: Mount of private directory return code [0]
Mar 14 16:05:39 zelda sshd[30151]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 16:05:39 zelda sshd[30141]: pam_unix(sshd:session): session closed for user trevor
Mar 14 16:05:39 zelda sshd[30141]: Mount of private directory return code [0]
Mar 14 16:05:44 zelda sshd[30178]: pam_sm_authenticate: Called 
Mar 14 16:05:44 zelda sshd[30178]: pam_sm_authenticate: username = [trevor] 
Mar 14 16:05:44 zelda sshd[30178]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 16:05:48 zelda sshd[30180]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:05:48 zelda sshd[30180]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 16:05:48 zelda sshd[30180]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 16:05:50 zelda sshd[30180]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:05:50 zelda sshd[30180]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 16:05:50 zelda sshd[30180]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 16:05:50 zelda sshd[30180]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 16:05:50 zelda sshd[30178]: Accepted password for trevor from 192.168.0.101 port 1381 ssh2
Mar 14 16:05:50 zelda sshd[30178]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 16:05:50 zelda sshd[30178]: Mount of private directory return code [0]
Mar 14 16:05:52 zelda sshd[30208]: Accepted publickey for trevor from 192.168.0.101 port 1385 ssh2
Mar 14 16:05:52 zelda sshd[30208]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 16:05:52 zelda sshd[30208]: Mount of private directory return code [0]
Mar 14 16:06:14 zelda sshd[30190]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 16:06:14 zelda sshd[30178]: pam_unix(sshd:session): session closed for user trevor
Mar 14 16:06:14 zelda sshd[30178]: Mount of private directory return code [0]
Mar 14 16:06:17 zelda sshd[30217]: Received disconnect from 192.168.0.101: 11: disconnected by user
Mar 14 16:06:17 zelda sshd[30208]: pam_unix(sshd:session): session closed for user trevor
Mar 14 16:06:17 zelda sshd[30208]: Mount of private directory return code [0]
Mar 14 16:08:05 zelda sshd[30252]: pam_sm_authenticate: Called 
Mar 14 16:08:05 zelda sshd[30252]: pam_sm_authenticate: username = [trevor] 
Mar 14 16:08:05 zelda sshd[30252]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 16:08:09 zelda sshd[30254]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:08:09 zelda sshd[30254]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 16:08:09 zelda sshd[30254]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 16:08:11 zelda sshd[30254]: Passphrase key already in keyring; rc = [1] 
Mar 14 16:08:11 zelda sshd[30254]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 16:08:11 zelda sshd[30254]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 16:08:11 zelda sshd[30254]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 16:08:11 zelda sshd[30252]: Accepted password for trevor from 192.168.0.101 port 1430 ssh2
Mar 14 16:08:11 zelda sshd[30252]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 16:08:11 zelda sshd[30252]: Mount of private directory return code [0]
Mar 14 16:08:23 zelda sudo:   trevor : TTY=pts/0 ; PWD=/home/trevor ; USER=root ; COMMAND=/bin/grep ssh /var/log/auth.log

```

---

### Post by digitrev on 2010-03-14
Here's a better dump of the logs.

This section deals with the first login attempt where it requires my password.
```

Mar 14 17:06:47 zelda sshd[31766]: pam_sm_authenticate: Called 
Mar 14 17:06:47 zelda sshd[31766]: pam_sm_authenticate: username = [trevor] 
Mar 14 17:06:47 zelda sshd[31766]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Mar 14 17:06:51 zelda sshd[31768]: Passphrase key already in keyring; rc = [1] 
Mar 14 17:06:51 zelda sshd[31768]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ce3ec5b7334a22f5] to the keyring; rc = [1] 
Mar 14 17:06:51 zelda sshd[31768]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Mar 14 17:06:53 zelda sshd[31768]: Passphrase key already in keyring; rc = [1] 
Mar 14 17:06:53 zelda sshd[31768]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [e3b4235f815eca29] to the keyring; rc = [1] 
Mar 14 17:06:53 zelda sshd[31768]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Mar 14 17:06:53 zelda sshd[31768]: There is already a key in the user session keyring for the given passphrase. 
Mar 14 17:06:53 zelda sshd[31766]: Accepted password for trevor from 192.168.0.101 port 2560 ssh2
Mar 14 17:06:53 zelda sshd[31766]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 17:06:53 zelda sshd[31766]: Mount of private directory return code [0]

```

This section deals with the second login attempt. This is while there is already a connection open to the remote box, zelda.
```

Mar 14 17:18:47 zelda sshd[32008]: Accepted publickey for trevor from 192.168.0.101 port 2872 ssh2
Mar 14 17:18:47 zelda sshd[32008]: pam_unix(sshd:session): session opened for user trevor by (uid=0)
Mar 14 17:18:47 zelda sshd[32008]: Mount of private directory return code [0]
Mar 14 17:19:13 zelda sudo:   trevor : TTY=pts/0 ; PWD=/home/trevor ; USER=root ; COMMAND=/bin/grep ssh /var/log/auth.log

```

---

### Post by digitrev on 2010-10-06
Six months later; same problem. Anybody able to help me?

---

### Post by r939ick on 2010-10-06
Could this be the issue?

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427)

---

### Post by luvshines on 2010-10-06
Also, if you could try with ssh -vv to generate more logs

---

### Post by digitrev on 2010-10-06
> **r939ick said:**
> Could this be the issue?

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427)
That is exactly the problem. Thank you very much, good sir.

---

