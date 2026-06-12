---
title: "Ssh over a slow connection"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by devent on 2012-03-24
Hello,
I have problems connecting to my server via ssh over a Globe Tattoo wireless G3. If I try from the Wireless in the next hotel it all works well, I also try to disable the firewall from my server. Here is the full (successful connection from the hotel's wireless) ssh -vvv log.

On the Globe Tattoo the log will stop at one the lines. I waited long (10 minutes and more) but there is no connection. I also try to connect to the virtual server host (Linode), but the ssh log will hold at the same lines, so it's not my sshd configuration or my firewall.

```
debug1: Entering interactive session.
```
```
debug2: we sent a publickey packet, wait for reply
```
```
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
```

Maybe someone can help me, because I really need to access ssh with the Globe Tattoo.


```
OpenSSH_5.8p2, OpenSSL 1.0.0g-fips 18 Jan 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to anr-institute.com [109.74.199.100] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/devent/.ssh/id_rsa" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/devent/.ssh/id_rsa type 1
debug1: identity file /home/devent/.ssh/id_rsa-cert type -1
debug1: identity file /home/devent/.ssh/id_dsa type -1
debug1: identity file /home/devent/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "anr-institute.com" from file "/home/devent/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/devent/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 139/256
debug2: bits set: 517/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 1c:52:70:97:9a:ed:7b:ca:bc:21:c4:2a:80:6d:66:9a
debug3: load_hostkeys: loading entries for host "anr-institute.com" from file "/home/devent/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/devent/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "109.74.199.100" from file "/home/devent/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/devent/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'anr-institute.com' is known and matches the RSA host key.
debug1: Found key in /home/devent/.ssh/known_hosts:1
debug2: bits set: 499/1024
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
debug2: key: /home/devent/.ssh/id_rsa (0x21ad0648)
debug2: key: /home/devent/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/devent/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp 87:6a:c3:1d:63:b0:ff:48:9f:06:3e:f6:0e:61:3b:4d
debug3: sign_and_send_pubkey: RSA 87:6a:c3:1d:63:b0:ff:48:9f:06:3e:f6:0e:61:3b:4d
debug1: Authentication succeeded (publickey).
Authenticated to anr-institute.com ([109.74.199.100]:22).
debug2: fd 6 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env GIT_PS1_SHOWDIRTYSTATE
debug3: Ignored env XDG_VTNR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env XDG_SESSION_ID
debug3: Ignored env JDEPEND_HOME
debug3: Ignored env KDE_MULTIHEAD
debug3: Ignored env HOSTNAME
debug3: Ignored env DM_CONTROL
debug3: Ignored env M2
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env XDG_MENU_PREFIX
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env HISTSIZE
debug3: Ignored env XDM_MANAGED
debug3: Ignored env GTK2_RC_FILES
debug3: Ignored env KONSOLE_DBUS_SERVICE
debug3: Ignored env GS_LIB
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env QTDIR
debug3: Ignored env SHELL_SESSION_ID
debug3: Ignored env QTINC
debug3: Ignored env KDE_FULL_SESSION
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env _JAVA_OPTIONS
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env MAIL
debug3: Ignored env PATH
debug3: Ignored env PWD
debug3: Ignored env EDITOR
debug3: Ignored env KDE_SESSION_UID
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env KDE_IS_PRELINKED
debug3: Ignored env KDEDIRS
debug3: Ignored env KONSOLE_DBUS_SESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SSH_ASKPASS
debug3: Ignored env HOME
debug3: Ignored env COLORFGBG
debug3: Ignored env XDG_SEAT
debug3: Ignored env M2_HOME
debug3: Ignored env SHLVL
debug3: Ignored env KDE_SESSION_VERSION
debug1: Sending env LANGUAGE = 
debug2: channel 0: request env confirm 0
debug3: Ignored env XCURSOR_THEME
debug3: Ignored env LOGNAME
debug3: Ignored env VISUAL
debug3: Ignored env CVS_RSH
debug3: Ignored env QTLIB
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env PROFILEHOME
debug3: Ignored env XDG_RUNTIME_DIR
debug3: Ignored env DISPLAY
debug3: Ignored env QT_PLUGIN_PATH
debug3: Ignored env ARCHIVA_HOME
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug1: channel 0: forcing write
debug3: channel 0: will not send data after close
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cc -1)

debug1: fd 2 clearing O_NONBLOCK
Connection to anr-institute.com closed.
Transferred: sent 2784, received 2456 bytes, in 15.4 seconds
Bytes per second: sent 180.5, received 159.3
debug1: Exit status 0

```

---

