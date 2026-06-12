---
title: "SSH hanging after upgrade to Ubuntu 11.04"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by danbicknell on 2011-05-03
I've been searching the internet for similar issues and haven't found an answer yet.

Recently I upgraded to Ubuntu 11.04 on my home server.  Before this, SSH worked fine.  Now, however, I get to 'Entering Interactive Session' and SSHD seems to hang.  I'll post a debug view below.

 dbicknel@spectre:~$ ssh -v -v -v -p XX 192.168.XX.X  (masking port and IP for security)
  OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
  debug1: Reading configuration data /etc/ssh/ssh_config
  debug1: Applying options for *
  debug2: ssh_connect: needpriv 0
  debug1: Connecting to 192.168.XX.X   [192.168.XX.X] port XXXX. (masking port and IP for security)
  debug1: Connection established.
  debug1: identity file /home/dbicknel/.ssh/id_rsa type -1
  debug1: identity file /home/dbicknel/.ssh/id_rsa-cert type -1
  debug1: identity file /home/dbicknel/.ssh/id_dsa type -1
  debug1: identity file /home/dbicknel/.ssh/id_dsa-cert type -1
  debug1: identity file /home/dbicknel/.ssh/id_ecdsa type -1
  debug1: identity file /home/dbicknel/.ssh/id_ecdsa-cert type -1
  debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
  debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
  debug1: Enabling compatibility mode for protocol 2.0
  debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
  debug2: fd 3 setting O_NONBLOCK
  debug3: put_host_port: [192.168.XX.X]:XXXX
  debug3: load_hostkeys: loading entries for host "[192.168.XX.X]:XXXX" from file "/home/dbicknel/.ssh/known_hosts"
  debug3: load_hostkeys: found key type RSA in file /home/dbicknel/.ssh/known_hosts:6
  debug3: load_hostkeys: loaded 1 keys
  debug3: order_hostkeyalgs: prefer hostkeyalgs: [EMAIL="ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa"]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa[/EMAIL]
  debug1: SSH2_MSG_KEXINIT sent
  debug1: SSH2_MSG_KEXINIT received
  debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
  debug2: kex_parse_kexinit: [EMAIL="ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss"]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss[/EMAIL]
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
  debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
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
  debug1: sending SSH2_MSG_KEX_ECDH_INIT
  debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
  debug1: Server host key: RSA 39:d6:80:1f:3a:d4:2c:39:af:aa:09:3e:42:38:9d:0f
  debug3: put_host_port: [192.168.66.7]:6693
  debug3: put_host_port: [192.168.66.7]:6693
  debug3: load_hostkeys: loading entries for host "[192.168.XX.X]:XXXX" from file "/home/dbicknel/.ssh/known_hosts"
  debug3: load_hostkeys: found key type RSA in file /home/dbicknel/.ssh/known_hosts:6
  debug3: load_hostkeys: loaded 1 keys
  debug3: load_hostkeys: loading entries for host "[192.168.XX.X]:XXXX" from file "/home/dbicknel/.ssh/known_hosts"
  debug3: load_hostkeys: found key type RSA in file /home/dbicknel/.ssh/known_hosts:6
  debug3: load_hostkeys: loaded 1 keys
  debug1: Host '[192.168.XX.X]:XXXX ' is known and matches the RSA host key.
  debug1: Found key in /home/dbicknel/.ssh/known_hosts:6
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
  debug2: key: /home/dbicknel/.ssh/id_rsa ((nil))
  debug2: key: /home/dbicknel/.ssh/id_dsa ((nil))
  debug2: key: /home/dbicknel/.ssh/id_ecdsa ((nil))
  debug1: Authentications that can continue: publickey,password
  debug3: start over, passed a different list publickey,password
  debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
  debug3: authmethod_lookup publickey
  debug3: remaining preferred: keyboard-interactive,password
  debug3: authmethod_is_enabled publickey
  debug1: Next authentication method: publickey
  debug1: Trying private key: /home/dbicknel/.ssh/id_rsa
  debug3: no such identity: /home/dbicknel/.ssh/id_rsa
  debug1: Trying private key: /home/dbicknel/.ssh/id_dsa
  debug3: no such identity: /home/dbicknel/.ssh/id_dsa
  debug1: Trying private key: /home/dbicknel/.ssh/id_ecdsa
  debug3: no such identity: /home/dbicknel/.ssh/id_ecdsa
  debug2: we did not send a packet, disable method
  debug3: authmethod_lookup password
  debug3: remaining preferred: ,password
  debug3: authmethod_is_enabled password
  debug1: Next authentication method: password [EMAIL="dbicknel@192.168.66.7%27s"]dbicknel@192.168.66.7's[/EMAIL] password: 
  debug3: packet_send2: adding 48 (len 61 padlen 19 extra_pad 64)
  debug2: we sent a password packet, wait for reply
  debug1: Authentication succeeded (password).
  Authenticated to 192.168.XX.X ([192.168.XX.X]:XXXX).
  debug1: channel 0: new [client-session]
  debug3: ssh_session2_open: channel_new: 0
  debug2: channel 0: send open
  debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
  debug1: Entering interactive session.
   
   
  Any help is appreciated!
   
  Thanks,
  Dan

---

### Post by sirphilip on 2011-05-16
I am having the same problem. I know it is a problem with my laptop and not the server as I can connect through ssh fine from other computers. I also installed putty on this laptop and I could connect to my server just fine

Macbook pro 4,1 and Ubuntu 11.04 on both my laptop and the server.

I've tried it locally and over the internet, both don't work.

Here is my -vvv output

```
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.2.150 [192.168.2.150] port 22.
debug1: Connection established.
debug1: identity file /home/jack/.ssh/id_rsa type -1
debug1: identity file /home/jack/.ssh/id_rsa-cert type -1
debug1: identity file /home/jack/.ssh/id_dsa type -1
debug1: identity file /home/jack/.ssh/id_dsa-cert type -1
debug1: identity file /home/jack/.ssh/id_ecdsa type -1
debug1: identity file /home/jack/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.2.150" from file "/home/jack/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/jack/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
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
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
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
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 43:2d:cb:9f:71:cc:0d:92:29:21:86:5d:a0:27:f3:98
debug3: load_hostkeys: loading entries for host "192.168.2.150" from file "/home/jack/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/jack/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.2.150' is known and matches the ECDSA host key.
debug1: Found key in /home/jack/.ssh/known_hosts:2
debug1: ssh_ecdsa_verify: signature correct
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
debug2: key: /home/jack/.ssh/id_rsa ((nil))
debug2: key: /home/jack/.ssh/id_dsa ((nil))
debug2: key: /home/jack/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jack/.ssh/id_rsa
debug3: no such identity: /home/jack/.ssh/id_rsa
debug1: Trying private key: /home/jack/.ssh/id_dsa
debug3: no such identity: /home/jack/.ssh/id_dsa
debug1: Trying private key: /home/jack/.ssh/id_ecdsa
debug3: no such identity: /home/jack/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
sa@192.168.2.150's password: 
debug3: packet_send2: adding 64 (len 55 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to 192.168.2.150 ([192.168.2.150]:22).
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
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug3: Ignored env GNOME_KEYRING_PID
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GDM_LANG
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env COMPIZ_CONFIG_PROFILE
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: client_check_window_change: changed
debug2: channel 0: request window-change confirm 0

```

---

### Post by Inquisitor on 2011-05-17
This sounds like it might be an issue I came across -- a conflict between certain versions of sshd and some Cisco network hardware.

More details:
[http://www.held.org.il/blog/2011/05/the-myterious-case-of-broken-ssh-client-connection-reset-by-peer/](http://www.held.org.il/blog/2011/05/the-myterious-case-of-broken-ssh-client-connection-reset-by-peer/)

An apparent workaround:
[https://www.nowhere.dk/articles/natty-narwhal-problems-connecting-to-servers-behind-cisco-firewalls-using-ssh](https://www.nowhere.dk/articles/natty-narwhal-problems-connecting-to-servers-behind-cisco-firewalls-using-ssh)

---

### Post by youknowit on 2011-05-18
Thank you so much! In my case, both the server and the client are Natty and I have had the same issue.  Your work around fixed it.

---

### Post by asterix404 on 2011-05-25
So this work around worked for me, just as a questions though, what did this do and why did this work? My sshd conf file didn't have anything uncommented for cyphers or for MACs. 

I mean why would having as cyphers arcfour256,arcfour128 break ssh or at least cause a stall? 

Thanks so much.

---

### Post by kingair_six on 2011-06-15
tried the workaround, still no success. this is really annoying since it keeps me from working efficiently (have to use FTP to bypass this bug). I'd love to work remotely on my projects via sshfs but can't. surely there must be a solution?

---

