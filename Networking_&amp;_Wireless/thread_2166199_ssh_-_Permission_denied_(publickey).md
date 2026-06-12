---
title: "ssh - Permission denied (publickey)"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by gatnos on 2013-08-08
I can't connect with the user sftp per ssh. I always get "Permission denied (publickey)."
I can connect with an other user without any problem.
I don't know what's wrong. 

When I start ssh via "/usr/sbin/sshd -d" there's the following message.
But as far as I see, the permissions are fine.

```
debug1: trying public key file /home/sftp/.ssh/authorized_keys
debug1: Could not open authorized keys '/home/sftp/.ssh/authorized_keys': Permission denied
```

Pls help,

Thank you.

```
root@foo /home # ll
total 20
drw-r-xr-x  5 root  root  4096 Apr 22 13:49 .
drwxrwx--- 23 pi    pi    4096 Aug  8 11:44 ..
drwx------ 16 pi    pi    4096 Aug  8 11:28 pi
drwxr-x---  3 rsync rsync 4096 Apr 22 18:22 rsync
drwxr-x---  6 sftp  sftp  4096 Aug  8 12:36 sftp
```


```
root@foo /home/sftp # ll
total 24
drwxr-x--- 6 sftp sftp 4096 Aug  8 12:36 .
drw-r-xr-x 5 root root 4096 Apr 22 13:49 ..
drwx------ 2 root root 4096 Aug  7 13:06 auth
drwx------ 2 sftp sftp 4096 Aug  8 11:34 .ssh
drwx------ 3 root root 4096 Aug  8 12:36 tes
drwxrwx--- 4 sftp sftp 4096 Aug  8 09:29 upload
```

```
root@foo /home/sftp/.ssh # ll
total 12
drwx------ 2 sftp sftp 4096 Aug  8 11:34 .
drwxr-x--- 6 sftp sftp 4096 Aug  8 12:36 ..
-rw------- 1 sftp sftp  394 Aug  8 10:20 authorized_keys
```

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
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel DEBUG3
#INFO

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

Match User sftp
ChrootDirectory /home/sftp
ForceCommand internal-sftp
```

/etc/init.d/ssh start
```
Aug  8 12:53:45 foo sshd[13047]: Set /proc/self/oom_score_adj from 0 to -1000
Aug  8 12:53:45 foo sshd[13047]: debug2: fd 3 setting O_NONBLOCK
Aug  8 12:53:45 foo sshd[13047]: debug1: Bind to port 22 on 0.0.0.0.
Aug  8 12:53:45 foo sshd[13047]: Server listening on 0.0.0.0 port 22.
Aug  8 12:53:45 foo sshd[13047]: socket: Address family not supported by protocol
Aug  8 12:53:57 foo sshd[13047]: debug3: fd 4 is not O_NONBLOCK
Aug  8 12:53:57 foo sshd[13047]: debug1: Forked child 13053.
Aug  8 12:53:57 foo sshd[13047]: debug3: send_rexec_state: entering fd = 7 config len 782
Aug  8 12:53:57 foo sshd[13047]: debug3: ssh_msg_send: type 0
Aug  8 12:53:57 foo sshd[13047]: debug3: send_rexec_state: done
Aug  8 12:53:57 foo sshd[13053]: debug3: oom_adjust_restore
Aug  8 12:53:57 foo sshd[13053]: Set /proc/self/oom_score_adj to 0
Aug  8 12:53:57 foo sshd[13053]: debug1: rexec start in 4 out 4 newsock 4 pipe 6 sock 7
Aug  8 12:53:57 foo sshd[13053]: debug1: inetd sockets after dupping: 3, 3
Aug  8 12:53:57 foo sshd[13053]: Connection from zzz.zzz.zzz.zzz port 34187
Aug  8 12:53:57 foo sshd[13053]: debug1: Client protocol version 2.0; client software version SSHJ_0_8_1_SNAPSHOT
Aug  8 12:53:57 foo sshd[13053]: debug1: no match: SSHJ_0_8_1_SNAPSHOT
Aug  8 12:53:57 foo sshd[13053]: debug1: Enabling compatibility mode for protocol 2.0
Aug  8 12:53:57 foo sshd[13053]: debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-4
Aug  8 12:53:57 foo sshd[13053]: debug2: fd 3 setting O_NONBLOCK
Aug  8 12:53:57 foo sshd[13053]: debug2: Network child is on pid 13056
Aug  8 12:53:57 foo sshd[13053]: debug3: preauth child monitor started
Aug  8 12:53:57 foo sshd[13053]: debug3: privsep user:group 101:65534 [preauth]
Aug  8 12:53:57 foo sshd[13053]: debug1: permanently_set_uid: 101/65534 [preauth]
Aug  8 12:53:57 foo sshd[13053]: debug1: list_hostkey_types: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256 [preauth]
Aug  8 12:53:57 foo sshd[13053]: debug1: SSH2_MSG_KEXINIT sent [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug1: SSH2_MSG_KEXINIT received [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: none,zlib@openssh.com [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: none,zlib@openssh.com [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit:  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit:  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: first_kex_follows 0  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: reserved 0  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: ssh-rsa,ssh-dss [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc,blowfish-cbc [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc,blowfish-cbc [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,hmac-md5-96 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,hmac-md5-96 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: none [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: none [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit:  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit:  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: first_kex_follows 0  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_parse_kexinit: reserved 0  [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: mac_setup: found hmac-sha1 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug1: kex: client->server aes128-ctr hmac-sha1 none [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: mac_setup: found hmac-sha1 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug1: kex: server->client aes128-ctr hmac-sha1 none [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: dh_gen_key: priv key bits set: 163/320 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: bits set: 1042/2048 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug1: expecting SSH2_MSG_KEXDH_INIT [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: bits set: 1050/2048 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_key_sign entering [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_request_send entering: type 5 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_request_receive entering
Aug  8 12:53:58 foo sshd[13053]: debug3: monitor_read: checking request 5
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_answer_sign
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_answer_sign: signature 0xb8788138(271)
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_request_send entering: type 6
Aug  8 12:53:58 foo sshd[13053]: debug2: monitor_read: 5 used once, disabling now
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_key_sign: waiting for MONITOR_ANS_SIGN [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_request_receive_expect entering: type 6 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug3: mm_request_receive entering [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: kex_derive_keys [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug2: set_newkeys: mode 1 [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug1: SSH2_MSG_NEWKEYS sent [preauth]
Aug  8 12:53:58 foo sshd[13053]: debug1: expecting SSH2_MSG_NEWKEYS [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug2: set_newkeys: mode 0 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug1: SSH2_MSG_NEWKEYS received [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug1: KEX done [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug1: userauth-request for user sftp service ssh-connection method publickey [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug1: attempt 0 failures 0 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_getpwnamallow entering [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_send entering: type 7 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_getpwnamallow: waiting for MONITOR_ANS_PWNAM [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive_expect entering: type 8 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive entering [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive entering
Aug  8 12:53:59 foo sshd[13053]: debug3: monitor_read: checking request 7
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_answer_pwnamallow
Aug  8 12:53:59 foo sshd[13053]: debug3: Trying to reverse map address zzz.zzz.zzz.zzz.
Aug  8 12:53:59 foo sshd[13053]: debug2: parse_server_config: config reprocess config len 782
Aug  8 12:53:59 foo sshd[13053]: debug3: checking match for 'User sftp' user sftp host xxx.xxx.xxx.xxx addr zzz.zzz.zzz.zzz
Aug  8 12:53:59 foo sshd[13053]: debug1: user sftp matched 'User sftp' at line 90
Aug  8 12:53:59 foo sshd[13053]: debug3: match found
Aug  8 12:53:59 foo sshd[13053]: debug3: reprocess config:91 setting ChrootDirectory /home/sftp
Aug  8 12:53:59 foo sshd[13053]: debug3: reprocess config:92 setting ForceCommand internal-sftp
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_send entering: type 8
Aug  8 12:53:59 foo sshd[13053]: debug2: monitor_read: 7 used once, disabling now
Aug  8 12:53:59 foo sshd[13053]: debug2: input_userauth_request: setting up authctxt for sftp [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_start_pam entering [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_send entering: type 50 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_inform_authserv entering [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_send entering: type 3 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug2: input_userauth_request: try method publickey [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug1: test whether pkalg/pkblob are acceptable [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_key_allowed entering [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_send entering: type 21 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_key_allowed: waiting for MONITOR_ANS_KEYALLOWED [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive_expect entering: type 22 [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive entering [preauth]
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive entering
Aug  8 12:53:59 foo sshd[13053]: debug3: monitor_read: checking request 50
Aug  8 12:53:59 foo sshd[13053]: debug1: PAM: initializing for "sftp"
Aug  8 12:53:59 foo sshd[13053]: debug1: PAM: setting PAM_RHOST to "xxx.xxx.xxx.xxx"
Aug  8 12:53:59 foo sshd[13053]: debug1: PAM: setting PAM_TTY to "ssh"
Aug  8 12:53:59 foo sshd[13053]: debug2: monitor_read: 50 used once, disabling now
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive entering
Aug  8 12:53:59 foo sshd[13053]: debug3: monitor_read: checking request 3
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_answer_authserv: service=ssh-connection, style=, role=
Aug  8 12:53:59 foo sshd[13053]: debug2: monitor_read: 3 used once, disabling now
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_receive entering
Aug  8 12:53:59 foo sshd[13053]: debug3: monitor_read: checking request 21
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_answer_keyallowed entering
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_answer_keyallowed: key_from_blob: 0xb878b170
Aug  8 12:53:59 foo sshd[13053]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
Aug  8 12:53:59 foo sshd[13053]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
Aug  8 12:53:59 foo sshd[13053]: debug1: temporarily_use_uid: 1001/1002 (e=0/0)
Aug  8 12:53:59 foo sshd[13053]: debug1: temporarily_use_uid: 1001/1002 (e=0/0)
Aug  8 12:53:59 foo sshd[13053]: Failed publickey for sftp from zzz.zzz.zzz.zzz port 34187 ssh2
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_answer_keyallowed: key 0xb878b170 is not allowed
Aug  8 12:53:59 foo sshd[13053]: debug3: mm_request_send entering: type 22
Aug  8 12:53:59 foo sshd[13053]: debug2: userauth_pubkey: authenticated 0 pkalg ssh-rsa [preauth]
```

/usr/sbin/sshd -d
```

debug1: sshd version OpenSSH_6.0p1 Debian-4
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
socket: Address family not supported by protocol
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug1: inetd sockets after dupping: 3, 3
Connection from zzz.zzz.zzz.zzz port 47983
debug1: Client protocol version 2.0; client software version SSHJ_0_8_1_SNAPSHOT
debug1: no match: SSHJ_0_8_1_SNAPSHOT
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-4
debug1: permanently_set_uid: 101/65534 [preauth]
debug1: list_hostkey_types: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256 [preauth]
debug1: SSH2_MSG_KEXINIT sent [preauth]
debug1: SSH2_MSG_KEXINIT received [preauth]
debug1: kex: client->server aes128-ctr hmac-sha1 none [preauth]
debug1: kex: server->client aes128-ctr hmac-sha1 none [preauth]
debug1: expecting SSH2_MSG_KEXDH_INIT [preauth]
debug1: SSH2_MSG_NEWKEYS sent [preauth]
debug1: expecting SSH2_MSG_NEWKEYS [preauth]
debug1: SSH2_MSG_NEWKEYS received [preauth]
debug1: KEX done [preauth]
debug1: attempt 0 failures 0 [preauth]
debug1: user sftp matched 'User sftp' at line 90
debug1: test whether pkalg/pkblob are acceptable [preauth]
debug1: PAM: initializing for "sftp"
debug1: PAM: setting PAM_RHOST to "xxx.xxx.xxx.xxx"
debug1: PAM: setting PAM_TTY to "ssh"
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: temporarily_use_uid: 1001/1002 (e=0/0)
debug1: trying public key file /home/sftp/.ssh/authorized_keys
debug1: Could not open authorized keys '/home/sftp/.ssh/authorized_keys': Permission denied
debug1: restore_uid: 0/0
debug1: temporarily_use_uid: 1001/1002 (e=0/0)
debug1: trying public key file /home/sftp/.ssh/authorized_keys2
debug1: Could not open authorized keys '/home/sftp/.ssh/authorized_keys2': Permission denied
debug1: restore_uid: 0/0
Failed publickey for sftp from zzz.zzz.zzz.zzz port 47983 ssh2
Received disconnect from zzz.zzz.zzz.zzz: 11:  [preauth]
debug1: do_cleanup [preauth]
debug1: monitor_read_log: child log fd closed
debug1: do_cleanup
debug1: PAM: cleanup
debug1: Killing privsep child 13201
```

---

### Post by Lars Noodén on 2013-08-08
Is the home directory set correctly for the user sftp?

```

grep sftp /etc/passwd

```

---

### Post by gatnos on 2013-08-08
Yes, it is. :-|
```
sftp:x:1001:1002:,,,:/home/sftp:/bin/false
```

---

### Post by Lars Noodén on 2013-08-08
I think that even with a key and using SFTP, if your shell is set to /bin/false you will not be able to log in.  Can you try setting the shell to /bin/bash or something temporarily to see if that works? 

If you want to make an SFTP-only account then that can be done with ForceCommand in sshd_config for a group or user.

---

### Post by gatnos on 2013-08-08
Changed /bin/false to /bin/bash,  /etc/init.d/ssh restart, no change at all.
Some time ago it was already working with this configuration. :-|

I don't get it, why the file and directory permissions are set to 600/700, but the file can't be accessed by ssh (/usr/sbin/sshd -d).
Or is it maybe a wrong log output? But that's the only clue I have.

PS. Sure I can't login because of /bin/false, but sftp/scp has to work.

---

### Post by steeldriver on 2013-08-08
Are you sure your permissions above /home/sftp are correct? your /home doesn't appear to be executable (openable) by its owner (root) and / appears to be owned by pi:pi

```

root@foo **/home # ll**
total 20
drw[SIZE=3][COLOR=#ff0000]**-**[/COLOR][/SIZE]r-xr-x  5 root  root  4096 Apr 22 13:49 [COLOR=#ff0000]**.**[/COLOR]
drwxrwx--- 23 [COLOR=#ff0000]pi    pi [/COLOR]   4096 Aug  8 11:44 [COLOR=#ff0000]**..**[/COLOR]
drwx------ 16 pi    pi    4096 Aug  8 11:28 pi
drwxr-x---  3 rsync rsync 4096 Apr 22 18:22 rsync
drwxr-x---  6 sftp  sftp  4096 Aug  8 12:36 sftp

```

---

### Post by gatnos on 2013-08-08
That's a good point. Should check this.
There are different results.

```
root@foo / # ll | grep home
drw-r-xr-x  6 root root  4096 Aug  8 14:39 home
```

---

### Post by gatnos on 2013-08-09
Still not sure why there were differend owner results but I was able to fix this.

When I set the authorized_keys permission to 644 instead of 600 everythink works fine.
I checked out some ssh connections I use, every authorized_keys file has 644 but 
from the man page of sshd it's not recommended and 600 should work although. :-|

Maybe someone knows this issue and can post a short answere, but my main problem is fixed.

---

