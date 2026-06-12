---
title: "SSH ignores &quot;StrictModes no&quot;"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by jordon on 2010-01-23
I'm trying to set up sshd. I had StrictModes set to "yes" and then changed it to "no." sshd seems to be reading the setting properly, as you can see below, but it's still refusing my public key when its permissions are set to 755.

Here's the debug output for sshd. (I deleted my IP address due to paranoia.) The values from my sshd_config file can be seen in the output.

```

$ sudo /usr/sbin/sshd -ddd -e
debug2: load_server_config: filename /etc/ssh/sshd_config
debug2: load_server_config: done config len = 843
debug2: parse_server_config: config /etc/ssh/sshd_config len 843
debug3: /etc/ssh/sshd_config:6 setting StrictModes no
debug3: /etc/ssh/sshd_config:11 setting Port 2727
debug3: /etc/ssh/sshd_config:14 setting AddressFamily inet
debug3: /etc/ssh/sshd_config:21 setting Protocol 2
debug3: /etc/ssh/sshd_config:24 setting X11Forwarding no
debug3: /etc/ssh/sshd_config:27 setting TCPKeepAlive no
debug3: /etc/ssh/sshd_config:28 setting ClientAliveInterval 600
debug3: /etc/ssh/sshd_config:29 setting ClientAliveCountMax 3
debug3: /etc/ssh/sshd_config:32 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:38 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:39 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:42 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:43 setting ServerKeyBits 768
debug3: /etc/ssh/sshd_config:46 setting PermitBlacklistedKeys no
debug3: /etc/ssh/sshd_config:52 setting AllowUsers jordon
debug3: /etc/ssh/sshd_config:55 setting LoginGraceTime 60
debug3: /etc/ssh/sshd_config:58 setting PermitRootLogin no
debug3: /etc/ssh/sshd_config:64 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:67 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:69 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:70 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:74 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:77 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:80 setting IgnoreUserKnownHosts yes
debug3: /etc/ssh/sshd_config:83 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:87 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:91 setting PasswordAuthentication no
debug3: /etc/ssh/sshd_config:97 setting UsePAM no
debug3: /etc/ssh/sshd_config:103 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:104 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:110 setting PrintMotd no
debug3: /etc/ssh/sshd_config:113 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:115 setting MaxAuthTries 2
debug3: /etc/ssh/sshd_config:117 setting MaxStartups 1
debug3: /etc/ssh/sshd_config:119 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug1: sshd version OpenSSH_5.1p1 Debian-6ubuntu2
debug3: Not a RSA1 key file /etc/ssh/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug1: rexec_argv[2]='-e'
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 2727 on 0.0.0.0.
Server listening on 0.0.0.0 port 2727.
debug3: fd 4 is not O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug3: send_rexec_state: entering fd = 7 config len 843
debug3: ssh_msg_send: type 0
debug3: send_rexec_state: done
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug3: recv_rexec_state: entering fd = 5
debug3: ssh_msg_recv entering
debug3: recv_rexec_state: done
debug2: parse_server_config: config rexec len 843
debug3: rexec:6 setting StrictModes no
debug3: rexec:11 setting Port 2727
debug3: rexec:14 setting AddressFamily inet
debug3: rexec:21 setting Protocol 2
debug3: rexec:24 setting X11Forwarding no
debug3: rexec:27 setting TCPKeepAlive no
debug3: rexec:28 setting ClientAliveInterval 600
debug3: rexec:29 setting ClientAliveCountMax 3
debug3: rexec:32 setting UsePrivilegeSeparation yes
debug3: rexec:38 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: rexec:39 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: rexec:42 setting KeyRegenerationInterval 3600
debug3: rexec:43 setting ServerKeyBits 768
debug3: rexec:46 setting PermitBlacklistedKeys no
debug3: rexec:52 setting AllowUsers jordon
debug3: rexec:55 setting LoginGraceTime 60
debug3: rexec:58 setting PermitRootLogin no
debug3: rexec:64 setting IgnoreRhosts yes
debug3: rexec:67 setting HostbasedAuthentication no
debug3: rexec:69 setting RSAAuthentication yes
debug3: rexec:70 setting PubkeyAuthentication yes
debug3: rexec:74 setting RhostsRSAAuthentication no
debug3: rexec:77 setting HostbasedAuthentication no
debug3: rexec:80 setting IgnoreUserKnownHosts yes
debug3: rexec:83 setting PermitEmptyPasswords no
debug3: rexec:87 setting ChallengeResponseAuthentication no
debug3: rexec:91 setting PasswordAuthentication no
debug3: rexec:97 setting UsePAM no
debug3: rexec:103 setting SyslogFacility AUTH
debug3: rexec:104 setting LogLevel INFO
debug3: rexec:110 setting PrintMotd no
debug3: rexec:113 setting PrintLastLog yes
debug3: rexec:115 setting MaxAuthTries 2
debug3: rexec:117 setting MaxStartups 1
debug3: rexec:119 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug1: sshd version OpenSSH_5.1p1 Debian-6ubuntu2
debug3: Not a RSA1 key file /etc/ssh/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: inetd sockets after dupping: 3, 3
Connection from [IP redacted] port 41085
debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug2: fd 3 setting O_NONBLOCK
debug3: privsep user:group 113:65534
debug1: permanently_set_uid: 113/65534
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug3: mm_request_send entering: type 0
debug3: mm_choose_dh: waiting for MONITOR_ANS_MODULI
debug3: mm_request_receive_expect entering: type 1
debug3: mm_request_receive entering
debug2: Network child is on pid 5255
debug3: preauth child monitor started
debug3: mm_request_receive entering
debug3: monitor_read: checking request 0
debug3: mm_answer_moduli: got parameters: 1024 1024 8192
debug3: mm_request_send entering: type 1
debug2: monitor_read: 0 used once, disabling now
debug3: mm_request_receive entering
debug3: mm_choose_dh: remaining 0
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug2: dh_gen_key: priv key bits set: 121/256
debug2: bits set: 509/1024
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug2: bits set: 500/1024
debug3: mm_key_sign entering
debug3: mm_request_send entering: type 5
debug3: mm_key_sign: waiting for MONITOR_ANS_SIGN
debug3: mm_request_receive_expect entering: type 6
debug3: mm_request_receive entering
debug3: monitor_read: checking request 5
debug3: mm_answer_sign
debug3: mm_answer_sign: signature 0x2523bf8(271)
debug3: mm_request_send entering: type 6
debug2: monitor_read: 5 used once, disabling now
debug3: mm_request_receive entering
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user jordon service ssh-connection method none
debug1: attempt 0 failures 0
debug3: mm_getpwnamallow entering
debug3: mm_request_send entering: type 7
debug3: mm_getpwnamallow: waiting for MONITOR_ANS_PWNAM
debug3: mm_request_receive_expect entering: type 8
debug3: mm_request_receive entering
debug3: monitor_read: checking request 7
debug3: mm_answer_pwnamallow
debug3: Trying to reverse map address [IP redacted].
debug2: parse_server_config: config reprocess config len 843
debug3: auth_shadow_acctexpired: today 14633 sp_expire -1 days left -14634
debug3: account expiration disabled
debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
debug3: mm_request_send entering: type 8
debug2: monitor_read: 7 used once, disabling now
debug3: mm_request_receive entering
debug2: input_userauth_request: setting up authctxt for jordon
debug3: mm_inform_authserv entering
debug3: mm_request_send entering: type 3
debug2: input_userauth_request: try method none
debug3: monitor_read: checking request 3
debug3: mm_answer_authserv: service=ssh-connection, style=, role=
debug2: monitor_read: 3 used once, disabling now
debug3: mm_request_receive entering
Connection closed by [IP redacted]
debug1: do_cleanup
debug1: do_cleanup

```

[Someone else]("http://marc.info/?l=secure-shell&m=112528280101025&w=2") seems to have had this problem, but it didn't seem to be solved. Can anyone help?

---

### Post by Pistolpete2 on 2012-06-15
EDIT: I mean this issues still occurs for me on Ubuntu 11.04

---

### Post by hawkmage on 2012-06-15
You are getting this because it is the ssh client that is throwing the error not the sshd server.

Keep in mind that the sshd_config controls the settings for the SSH Daemon where as the ssh_config controls the settings for the ssh client.

There is no directive for the ssh_config that I know of that disables this permissions check.  Let me tak a look a the source for OpenSSH and see if there is any thing there.

OK, looking at the code here is what I found:
The ssh command main function calls "key_load_private_type" for each type of private key supported which in turn calls key_perm_ok and if private key file owner UID doesn't match the current user UID and permissions have any bit for group or other set key_perm_ok prints that "UNPROTECTED PRIVATE KEY FILE" warning and returns False (0) to key_load_private_type.  This causes key_load_private_type to return a Null private key to the ssh main function which causes it to continue as if there was no private key to use for authentication.

There are no switches/or conditionals in the UID/Permission check on the private key done by the ssh client command so there is no way to override it.

---

### Post by Pistolpete2 on 2012-06-15
Please do not bother anymore :-).

The problem is solved.

I'd be happy to say way but I am not sure ;-).  The only thing I now that the host is rebooted so I gues that something went wrong when I restarted the SSH Daemon service.  My client configuration hasn't changed so I guess it was server-side instead of client side.

Which would be more logical to me because if you cannot setup your SSH connection you cannot check the permissions of the folders on the remote host.  So the client cannot determine the conditions that must be true (700 for home folder, .ssh folder and authorized_keys) for strictMode.

Thanks for your time, but sometimes a Microsoft solution (e.g. rebooting) does the trick :-D.

---

### Post by coffeecat on 2012-06-15
> **Pistolpete2 said:**
> 
The problem is solved.

Good to hear. I've closed this thread with a > 2-year old first post.

---

