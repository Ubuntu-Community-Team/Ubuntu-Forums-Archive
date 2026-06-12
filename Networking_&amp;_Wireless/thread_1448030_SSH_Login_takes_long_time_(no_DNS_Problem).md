---
title: "SSH Login takes long time (no DNS Problem)"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by a4fcorvus on 2010-04-06
Hi!

I have a problem with the ssh login to my server. After providing the password it hangs about 20 seconds before the prompt comes.

The ssh server i have started with following command:
>  /usr/sbin/sshd -p 55222 -D -ddd -eSSH Version Info:
> OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007The problem i have tracked down to the marked line (####) in the sshd debug dump (i think it has nothing to do with DNS).

> debug2: load_server_config: filename /etc/ssh/sshd_config
debug2: load_server_config: done config len = 631
debug2: parse_server_config: config /etc/ssh/sshd_config len 631
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:14 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:17 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:18 setting ServerKeyBits 768
debug3: /etc/ssh/sshd_config:21 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:22 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:25 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:26 setting PermitRootLogin yes
debug3: /etc/ssh/sshd_config:27 setting StrictModes yes
debug3: /etc/ssh/sshd_config:29 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:30 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:34 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:36 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:38 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:43 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:47 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:64 setting PrintMotd no
debug3: /etc/ssh/sshd_config:65 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:66 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:73 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:75 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:77 setting UsePAM yes
debug3: /etc/ssh/sshd_config:78 setting UseDNS no
debug1: sshd version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug3: Not a RSA1 key file /etc/ssh/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-p'
debug1: rexec_argv[2]='55222'
debug1: rexec_argv[3]='-D'
debug1: rexec_argv[4]='-ddd'
debug1: rexec_argv[5]='-e'
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 55222 on ::.
Server listening on :: port 55222.
debug2: fd 4 setting O_NONBLOCK
debug1: Bind to port 55222 on 0.0.0.0.
Bind to port 55222 on 0.0.0.0 failed: Address already in use.
debug3: fd 4 is not O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug3: send_rexec_state: entering fd = 7 config len 631
debug3: ssh_msg_send: type 0
debug3: send_rexec_state: done
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug3: recv_rexec_state: entering fd = 5
debug3: ssh_msg_recv entering
debug3: recv_rexec_state: done
debug2: parse_server_config: config rexec len 631
debug3: rexec:5 setting Port 22
debug3: rexec:9 setting Protocol 2
debug3: rexec:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: rexec:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: rexec:14 setting UsePrivilegeSeparation yes
debug3: rexec:17 setting KeyRegenerationInterval 3600
debug3: rexec:18 setting ServerKeyBits 768
debug3: rexec:21 setting SyslogFacility AUTH
debug3: rexec:22 setting LogLevel INFO
debug3: rexec:25 setting LoginGraceTime 120
debug3: rexec:26 setting PermitRootLogin yes
debug3: rexec:27 setting StrictModes yes
debug3: rexec:29 setting RSAAuthentication yes
debug3: rexec:30 setting PubkeyAuthentication yes
debug3: rexec:34 setting IgnoreRhosts yes
debug3: rexec:36 setting RhostsRSAAuthentication no
debug3: rexec:38 setting HostbasedAuthentication no
debug3: rexec:43 setting PermitEmptyPasswords no
debug3: rexec:47 setting ChallengeResponseAuthentication no
debug3: rexec:63 setting X11DisplayOffset 10
debug3: rexec:64 setting PrintMotd no
debug3: rexec:65 setting PrintLastLog yes
debug3: rexec:66 setting TCPKeepAlive yes
debug3: rexec:73 setting AcceptEnv LANG LC_*
debug3: rexec:75 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: rexec:77 setting UsePAM yes
debug3: rexec:78 setting UseDNS no
debug1: sshd version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug3: Not a RSA1 key file /etc/ssh/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: inetd sockets after dupping: 3, 3
debug3: Normalising mapped IPv4 in IPv6 address
debug3: Normalising mapped IPv4 in IPv6 address
Connection from 139.29.160.26 port 46683
debug1: Client protocol version 2.0; client software version OpenSSH_4.2p1 Debian-7ubuntu3.5
debug1: match: OpenSSH_4.2p1 Debian-7ubuntu3.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug3: privsep user:group 104:65534
debug1: permanently_set_uid: 104/65534
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: Network child is on pid 955
debug3: preauth child monitor started
debug3: mm_request_receive entering
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug3: mm_request_send entering: type 0
debug3: mm_choose_dh: waiting for MONITOR_ANS_MODULI
debug3: mm_request_receive_expect entering: type 1
debug3: mm_request_receive entering
debug3: monitor_read: checking request 0
debug3: mm_answer_moduli: got parameters: 1024 1024 8192
debug3: mm_request_send entering: type 1
debug3: mm_choose_dh: remaining 0
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug2: dh_gen_key: priv key bits set: 127/256
debug2: bits set: 535/1024
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug2: monitor_read: 0 used once, disabling now
debug3: mm_request_receive entering
debug2: bits set: 538/1024
debug3: mm_key_sign entering
debug3: mm_request_send entering: type 5
debug3: mm_key_sign: waiting for MONITOR_ANS_SIGN
debug3: mm_request_receive_expect entering: type 6
debug3: mm_request_receive entering
debug3: monitor_read: checking request 5
debug3: mm_answer_sign
debug3: mm_answer_sign: signature 0x7f5629a86510(271)
debug3: mm_request_send entering: type 6
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: monitor_read: 5 used once, disabling now
debug3: mm_request_receive entering
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user ACM service ssh-connection method none
debug1: attempt 0 failures 0
debug3: mm_getpwnamallow entering
debug3: mm_request_send entering: type 7
debug3: mm_getpwnamallow: waiting for MONITOR_ANS_PWNAM
debug3: mm_request_receive_expect entering: type 8
debug3: mm_request_receive entering
debug3: monitor_read: checking request 7
debug3: mm_answer_pwnamallow
debug2: parse_server_config: config reprocess config len 631
debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
debug3: mm_request_send entering: type 8
debug2: input_userauth_request: setting up authctxt for ACM
debug3: mm_start_pam entering
debug3: mm_request_send entering: type 48
debug3: mm_inform_authserv entering
debug3: mm_request_send entering: type 3
debug2: input_userauth_request: try method none
debug3: mm_auth_password entering
debug3: mm_request_send entering: type 11
debug3: mm_auth_password: waiting for MONITOR_ANS_AUTHPASSWORD
debug3: mm_request_receive_expect entering: type 12
debug3: mm_request_receive entering
debug2: monitor_read: 7 used once, disabling now
debug3: mm_request_receive entering
debug3: monitor_read: checking request 48
debug1: PAM: initializing for "ACM"
debug1: PAM: setting PAM_RHOST to "139.29.160.26"
debug1: PAM: setting PAM_TTY to "ssh"
debug2: monitor_read: 48 used once, disabling now
debug3: mm_request_receive entering
debug3: monitor_read: checking request 3
debug3: mm_answer_authserv: service=ssh-connection, style=, role=
debug2: monitor_read: 3 used once, disabling now
debug3: mm_request_receive entering
debug3: monitor_read: checking request 11
debug3: mm_answer_authpassword: sending result 0
debug3: mm_request_send entering: type 12
debug3: mm_auth_password: user not authenticated
Failed none for ACM from 139.29.160.26 port 46683 ssh2
debug3: mm_request_receive entering
debug1: userauth-request for user ACM service ssh-connection method password
debug1: attempt 1 failures 1
debug2: input_userauth_request: try method password
debug3: mm_auth_password entering
debug3: mm_request_send entering: type 11
debug3: mm_auth_password: waiting for MONITOR_ANS_AUTHPASSWORD
debug3: mm_request_receive_expect entering: type 12
debug3: mm_request_receive entering
debug3: monitor_read: checking request 11
debug3: PAM: sshpam_passwd_conv called with 1 messages
debug1: PAM: password authentication accepted for ACM
debug3: mm_answer_authpassword: sending result 1
debug3: mm_request_send entering: type 12
debug3: mm_auth_password: user authenticated
debug3: mm_do_pam_account entering
debug3: mm_request_send entering: type 49
debug3: mm_request_receive_expect entering: type 50
debug3: mm_request_receive entering
debug3: mm_request_receive_expect entering: type 49
debug3: mm_request_receive entering
debug1: do_pam_account: called
debug3: PAM: do_pam_account pam_acct_mgmt = 0 (Success)
debug3: mm_request_send entering: type 50
debug3: mm_do_pam_account returning 1
debug3: mm_send_keystate: Sending new keys: 0x7f5629a85d50 0x7f5629a7dc20
debug3: mm_newkeys_to_blob: converting 0x7f5629a85d50
debug3: mm_newkeys_to_blob: converting 0x7f5629a7dc20
debug3: mm_send_keystate: New keys have been sent
debug3: mm_send_keystate: Sending compression state
debug3: mm_request_send entering: type 25
debug3: mm_send_keystate: Finished sending state
Accepted password for ACM from 139.29.160.26 port 46683 ssh2
debug1: monitor_child_preauth: ACM has been authenticated by privileged process
debug3: mm_get_keystate: Waiting for new keys
debug3: mm_request_receive_expect entering: type 25
debug3: mm_request_receive entering
debug3: mm_newkeys_from_blob: 0x7f5629a8bd80(122)
debug2: mac_setup: found hmac-md5
debug3: mm_get_keystate: Waiting for second key
debug3: mm_newkeys_from_blob: 0x7f5629a8bd80(122)
debug2: mac_setup: found hmac-md5
debug3: mm_get_keystate: Getting compression state
debug3: mm_get_keystate: Getting Network I/O buffers
debug3: mm_share_sync: Share sync
debug3: mm_share_sync: Share sync end
debug2: User child is on pid 957

####################### HANGS AFTER THIS LINE ##########
debug3: mm_request_receive entering
##################################################

debug3: PAM: opening session
debug3: PAM: sshpam_store_conv called with 1 messages
debug1: PAM: establishing credentials
debug1: permanently_set_uid: 1002/1002
debug1: SELinux support disabled
debug2: set_newkeys: mode 0
debug2: set_newkeys: mode 1
debug1: Entering interactive session for SSH2.
debug2: fd 6 setting O_NONBLOCK
debug2: fd 7 setting O_NONBLOCK
debug1: server_init_dispatch_20
debug1: server_input_channel_open: ctype session rchan 0 win 65536 max 16384
debug1: input_session_request
debug1: channel 0: new [server-session]
debug1: session_new: init
debug1: session_new: session 0
debug1: session_open: channel 0
debug1: session_open: session 0: link with channel 0
debug1: server_input_channel_open: confirm session
debug1: server_input_channel_req: channel 0 request pty-req reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req pty-req
debug1: Allocating pty.
debug3: mm_request_send entering: type 26
debug3: mm_pty_allocate: waiting for MONITOR_ANS_PTY
debug3: mm_request_receive_expect entering: type 27
debug3: mm_request_receive entering
debug3: monitor_read: checking request 26
debug3: mm_answer_pty entering
debug1: session_new: init
debug1: session_new: session 0
debug1: SELinux support disabled
debug3: mm_request_send entering: type 27
debug3: mm_answer_pty: tty /dev/pts/2 ptyfd 4
debug3: mm_request_receive entering
debug1: session_pty_req: session 0 alloc /dev/pts/2
debug3: tty_parse_modes: SSH2 n_bytes 256
debug3: tty_parse_modes: ospeed 38400
debug3: tty_parse_modes: ispeed 38400
debug3: tty_parse_modes: 1 3
debug3: tty_parse_modes: 2 28
debug3: tty_parse_modes: 3 127
debug3: tty_parse_modes: 4 21
debug3: tty_parse_modes: 5 4
debug3: tty_parse_modes: 6 255
debug3: tty_parse_modes: 7 255
debug3: tty_parse_modes: 8 17
debug3: tty_parse_modes: 9 19
debug3: tty_parse_modes: 10 26
debug3: tty_parse_modes: 12 18
debug3: tty_parse_modes: 13 23
debug3: tty_parse_modes: 14 22
debug3: tty_parse_modes: 18 15
debug3: tty_parse_modes: 30 0
debug3: tty_parse_modes: 31 0
debug3: tty_parse_modes: 32 0
debug3: tty_parse_modes: 33 0
debug3: tty_parse_modes: 34 0
debug3: tty_parse_modes: 35 0
debug3: tty_parse_modes: 36 1
debug3: tty_parse_modes: 37 0
debug3: tty_parse_modes: 38 1
debug3: tty_parse_modes: 39 0
debug3: tty_parse_modes: 40 0
debug3: tty_parse_modes: 41 0
debug3: tty_parse_modes: 50 1
debug3: tty_parse_modes: 51 1
debug3: tty_parse_modes: 52 0
debug3: tty_parse_modes: 53 1
debug3: tty_parse_modes: 54 1
debug3: tty_parse_modes: 55 1
debug3: tty_parse_modes: 56 0
debug3: tty_parse_modes: 57 0
debug3: tty_parse_modes: 58 0
debug3: tty_parse_modes: 59 1
debug3: tty_parse_modes: 60 1
debug3: tty_parse_modes: 61 1
debug3: tty_parse_modes: 62 0
debug3: tty_parse_modes: 70 1
debug3: tty_parse_modes: 71 0
debug3: tty_parse_modes: 72 1
debug3: tty_parse_modes: 73 0
debug3: tty_parse_modes: 74 0
debug3: tty_parse_modes: 75 0
debug3: tty_parse_modes: 90 1
debug3: tty_parse_modes: 91 1
debug3: tty_parse_modes: 92 0
debug3: tty_parse_modes: 93 0
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug2: Setting env 0: LANG=de_DE
debug1: server_input_channel_req: channel 0 request shell reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req shell
debug1: PAM: setting PAM_TTY to "/dev/pts/2"
debug1: Setting controlling tty using TIOCSCTTY.
debug3: monitor_read: checking request 61
debug3: mm_answer_consolekit_register entering
debug1: session_by_tty: session 0 tty /dev/pts/2
debug1: Unable to open session: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
debug3: mm_request_send entering: type 62
debug3: mm_request_receive entering
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: rfd 9 isatty
debug2: fd 9 setting O_NONBLOCK
debug3: fd 8 is O_NONBLOCK
debug1: Received SIGCHLD.
debug1: session_by_pid: pid 979
debug1: session_exit_message: session 0 channel 0 pid 979
debug2: channel 0: request exit-status confirm 0
debug1: session_exit_message: release channel 0
debug2: channel 0: write failed
debug2: channel 0: close_write
debug2: channel 0: output open -> closed
debug3: mm_request_send entering: type 28
debug2: channel 0: read<=0 rfd 9 len -1
debug2: channel 0: read failed
debug2: channel 0: close_read
debug2: channel 0: input open -> drain
debug2: channel 0: ibuf empty
debug2: channel 0: send eof
debug2: channel 0: input drain -> closed
debug2: channel 0: send close
debug2: notify_done: reading
debug3: channel 0: will not send data after close
debug3: monitor_read: checking request 28
debug3: mm_answer_pty_cleanup entering
debug1: session_by_tty: session 0 tty /dev/pts/2
debug3: mm_session_close: session 0 pid 957
debug3: mm_session_close: tty /dev/pts/2 ptyfd 4
debug1: session_pty_cleanup: session 0 release /dev/pts/2
debug1: unregistering ConsoleKit session (null)
debug3: mm_request_receive entering
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: is dead
debug2: channel 0: gc: notify user
debug1: session_by_channel: session 0 channel 0
debug1: session_close_by_channel: channel 0 child 0
debug1: session_close: session 0 pid 0
debug2: channel 0: gc: user detached
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: server-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 server-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e -1 c -1
Connection closed by 139.29.160.26
debug1: do_cleanup
debug1: PAM: cleanup
debug3: PAM: sshpam_thread_cleanup entering
Closing connection to 139.29.160.26
debug1: PAM: cleanup
debug3: mm_request_send entering: type 63
debug3: monitor_read: checking request 63
debug3: mm_answer_term: tearing down sessions


On client side the debug output for the line is:

> ACM@arus054's password:
debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.

Have somebody any idea how to solve this problem?
If you need more information let me know :)

ty

---

### Post by pedemoz on 2010-05-14
I had a similar problem of slow ssh login, but mine was stopping after "Entering interactive session" (a few lines after where you indicated the delay in your log).  So it's probably not the same issue but you may still want to check the bug report and solution on Launchpad... [https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930](https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930)

---

### Post by HerbCSO on 2010-10-27
Have you tried the UseDNS No option? (see [http://ubuntuforums.org/showthread.php?t=630623](http://ubuntuforums.org/showthread.php?t=630623) ) - that worked for me just now.

---

### Post by erikdhansen on 2011-01-26
So I was having this same problem and it wasn't the DNS issue that everyone points to.  It ended up being a problem with PAM.

I was able to verify this by noting that telnet logins also took a long time to establish and PAM appeared to be the culprit there, as well.  However, cron didn't see delays with PAM when it ran.  Looking at the difference in PAM configurations for cron vs. sshd revealed a line in common-session that turned out to be the problem.


```
 and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
#session	optional			pam_ck_connector.so nox11
```

It was the PAM CK connector that was introducing the delay.  Commenting out that connector got rid of the delay in my case.

---

### Post by mlkrime on 2011-07-21
I tried UseDNS no, and it didn't work.

putting the option "GSSAPIAuthentication no" instead "yes" in the /etc/ssh/ssh_config file.

from: [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/84899](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/84899)

this worked for me.

---

### Post by ravip on 2012-07-05
it works for me .....:) thq...

---

### Post by ravip on 2012-07-05
> **HerbCSO said:**
> Have you tried the UseDNS No option? (see [http://ubuntuforums.org/showthread.php?t=630623](http://ubuntuforums.org/showthread.php?t=630623) ) - that worked for me just now.

--- it's work for me ... thq very much...

ravi

---

### Post by wildmanne39 on 2012-07-05
Old thread closed.

---

