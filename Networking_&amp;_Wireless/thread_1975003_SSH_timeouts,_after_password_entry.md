---
title: "SSH timeouts, after password entry"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by Empire-Phoenix on 2012-05-06
Well I have a problem (it worked before fine) taht just showed up.

When using ssh do connect to my server, it answers with login promt almost instantly, and let me etner username & password. After I enterd the password nothing happens anymore at all, untill I get a Remote host closed connection.

The server itself seems to run fine, every service is responding as expected and the virtual amchines running on it are reachable normally as well.

Any ideas what might cause this kind of problem?
(Ans also how I can connect to it again?)

---

### Post by shofer on 2012-05-07
Hey, i have the same problem here.
Ubuntu 10.04.01 LTS with latest updates.

For 2 days i'm not able to login via ssh nor sftp.

Everything else is working, i also have access via KVM Console.

---

### Post by Lars Noodén on 2012-05-07
Have you tried looking for clues by running ssh in verbose mode?  (-v, -vv or -vvv)

---

### Post by Empire-Phoenix on 2012-05-07
Unfortunatly it looks not so good doing -vvv  (As aside note, server is using latest LTS version)


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
debug2: key: /home/remote/.ssh/id_rsa ((nil))
debug2: key: /home/remote/.ssh/id_dsa ((nil))
debug2: key: /home/remote/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/remote/.ssh/id_rsa
debug3: no such identity: /home/remote/.ssh/id_rsa
debug1: Trying private key: /home/remote/.ssh/id_dsa
debug3: no such identity: /home/remote/.ssh/id_dsa
debug1: Trying private key: /home/remote/.ssh/id_ecdsa
debug3: no such identity: /home/remote/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
---------------------------------------------(line of for better readability , of course not in original output)
[email]remote@xxx.xxx.xxx.xx[/email]'s password:
debug3: packet_send2: adding 48 (len 61 padlen 19 extra_pad 64)
debug2: we sent a password packet, wait for reply
(insert a almost 2 minute wait here)
Connection closed by xxx.xxx.xxx.xx

---

### Post by shofer on 2012-05-07
Server side auth.log output:

May  7 16:21:08 server sshd[15031]: debug3: fd 5 is not O_NONBLOCK
May  7 16:21:08 server sshd[15031]: debug1: Forked child 17210.
May  7 16:21:08 server sshd[15031]: debug3: send_rexec_state: entering fd = 9 config len 701
May  7 16:21:08 server sshd[15031]: debug3: ssh_msg_send: type 0
May  7 16:21:08 server sshd[15031]: debug3: send_rexec_state: done
May  7 16:21:08 server sshd[17210]: debug3: oom_adjust_restore
May  7 16:21:08 server sshd[17210]: Set /proc/self/oom_adj to -17
May  7 16:21:08 server sshd[17210]: debug1: rexec start in 5 out 5 newsock 5 pipe 8 sock 9
May  7 16:21:08 server sshd[17210]: debug1: inetd sockets after dupping: 3, 3
May  7 16:21:08 server sshd[17210]: debug1: Client protocol version 2.0; client software version OpenSSH_5.6
May  7 16:21:08 server sshd[17210]: debug1: match: OpenSSH_5.6 pat OpenSSH*
May  7 16:21:08 server sshd[17210]: debug1: Enabling compatibility mode for protocol 2.0
May  7 16:21:08 server sshd[17210]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7
May  7 16:21:08 server sshd[17210]: debug2: fd 3 setting O_NONBLOCK
May  7 16:21:08 server sshd[17210]: debug2: Network child is on pid 17211
May  7 16:21:08 server sshd[17210]: debug3: preauth child monitor started
May  7 16:21:08 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:08 server sshd[17210]: debug3: monitor_read: checking request 0
May  7 16:21:08 server sshd[17210]: debug3: mm_answer_moduli: got parameters: 1024 1024 8192
May  7 16:21:08 server sshd[17210]: debug3: mm_request_send entering: type 1
May  7 16:21:08 server sshd[17210]: debug2: monitor_read: 0 used once, disabling now
May  7 16:21:08 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:08 server sshd[17210]: debug3: monitor_read: checking request 4
May  7 16:21:08 server sshd[17210]: debug3: mm_answer_sign
May  7 16:21:08 server sshd[17210]: debug3: mm_answer_sign: signature 0x1b3f3d0(271)
May  7 16:21:08 server sshd[17210]: debug3: mm_request_send entering: type 5
May  7 16:21:08 server sshd[17210]: debug2: monitor_read: 4 used once, disabling now
May  7 16:21:08 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:09 server sshd[17210]: debug3: monitor_read: checking request 6
May  7 16:21:09 server sshd[17210]: debug3: mm_answer_pwnamallow
May  7 16:21:09 server sshd[17210]: debug3: Trying to reverse map address xxxxxxxxxxx.
May  7 16:21:09 server sshd[17210]: debug2: parse_server_config: config reprocess config len 701
May  7 16:21:09 server sshd[17210]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
May  7 16:21:09 server sshd[17210]: debug3: mm_request_send entering: type 7
May  7 16:21:09 server sshd[17210]: debug2: monitor_read: 6 used once, disabling now
May  7 16:21:09 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:09 server sshd[17210]: debug3: monitor_read: checking request 45
May  7 16:21:09 server sshd[17210]: debug1: PAM: initializing for "username"
May  7 16:21:09 server sshd[17210]: debug1: PAM: setting PAM_RHOST to "xxxxxxxxxxxxxxxxx"
May  7 16:21:09 server sshd[17210]: debug1: PAM: setting PAM_TTY to "ssh"
May  7 16:21:09 server sshd[17210]: debug2: monitor_read: 45 used once, disabling now
May  7 16:21:09 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:09 server sshd[17210]: debug3: monitor_read: checking request 3
May  7 16:21:09 server sshd[17210]: debug3: mm_answer_authserv: service=ssh-connection, style=
May  7 16:21:09 server sshd[17210]: debug2: monitor_read: 3 used once, disabling now
May  7 16:21:09 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:09 server sshd[17210]: debug3: monitor_read: checking request 10
May  7 16:21:09 server sshd[17210]: debug3: mm_answer_authpassword: sending result 0
May  7 16:21:09 server sshd[17210]: debug3: mm_request_send entering: type 11
May  7 16:21:09 server sshd[17210]: Failed none for server from xxxxxxxxxx port 49263 ssh2
May  7 16:21:09 server sshd[17210]: debug3: mm_request_receive entering
May  7 16:21:10 server sshd[17210]: debug3: monitor_read: checking request 10



Client Side output:

OpenSSH_5.6p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxxxxxxxxxxxxx [xxxxxxxxxxxxxxx] port 22.
debug1: Connection established.
debug1: identity file /Users/stefan/.ssh/id_rsa type -1
debug1: identity file /Users/stefan/.ssh/id_rsa-cert type -1
debug1: identity file /Users/stefan/.ssh/id_dsa type -1
debug1: identity file /Users/stefan/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.6
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
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
debug2: dh_gen_key: priv key bits set: 130/256
debug2: bits set: 493/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: host xxxxx  filename /Users/stefan/.ssh/known_hosts
debug3: check_host_in_hostfile: host xxxxx filename /Users/stefan/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 23
debug3: check_host_in_hostfile: host xxxxxxx filename /Users/stefan/.ssh/known_hosts
debug3: check_host_in_hostfile: host xxxxxxx filename /Users/stefan/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 23
debug1: Host 'xxxxxxxxx' is known and matches the RSA host key.
debug1: Found key in /Users/stefan/.ssh/known_hosts:23
debug2: bits set: 486/1024
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
debug2: key: /Users/stefan/.ssh/id_rsa (0x0)
debug2: key: /Users/stefan/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/stefan/.ssh/id_rsa
debug3: no such identity: /Users/stefan/.ssh/id_rsa
debug1: Trying private key: /Users/stefan/.ssh/id_dsa
debug3: no such identity: /Users/stefan/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
xxxxxxxxxxxxxx@xxxxxxxxxxxxxxx's password: 
debug3: packet_send2: adding 64 (len 59 padlen 5 extra_pad 64)
debug2: we sent a password packet, wait for reply
(2 minutes waiting)
Connection closed by xxx


i have no idea what i could check next...

---

### Post by Empire-Phoenix on 2012-05-07
I would like to provide server side information as well, unfortunatly the server is only reachable by ssh (or by car)

(And maybee after a reboot, but I won't risk rebooting it, if its not reachable after that/no solution is found, and the services it provides are offline)

---

### Post by shofer on 2012-05-08
so..i've tried a lot, but it still not work.

I've increased login timeout.. so sometimes i can get in after 2-4 Minutes of waiting.

Than i've tried to turn of UseDNS, which does not help.
Now i tried public key login.. and.. this works..

but I need Password Authentication as well... any ideas?

Thanks a lot!

---

### Post by gaurang171 on 2012-05-09
Hi I am also facing the same issue. once i entered password i dont get any response. 
even if enter worng password it never says its wrong. any help is appreciated

Here is my debug
```

debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to mediagun.com [174.37.211.146] port 22.
debug1: Connection established.
debug1: identity file /Users/crazy/.ssh/identity type -1
debug1: identity file /Users/crazy/.ssh/id_rsa type -1
debug1: identity file /Users/crazy/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'mediagun.com' is known and matches the RSA host key.
debug1: Found key in /Users/crazy/.ssh/known_hosts:8
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/crazy/.ssh/identity
debug1: Trying private key: /Users/crazy/.ssh/id_rsa
debug1: Trying private key: /Users/crazy/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password: 
```

---

### Post by mexys on 2012-05-10
I have the same problem too. Yesterday it worked fine. I didn't change some confings and didn't reboot the system. But today I can not log in.

auth.log
```

May 10 22:47:08 home sshd[5799]: debug1: inetd sockets after dupping: 3, 3
May 10 22:47:08 home sshd[5799]: debug1: Client protocol version 2.0; client software version PuTTY_Snapshot_2011_07_13:r9206
May 10 22:47:08 home sshd[5799]: debug1: no match: PuTTY_Snapshot_2011_07_13:r9206
May 10 22:47:08 home sshd[5799]: debug1: Enabling compatibility mode for protocol 2.0
May 10 22:47:08 home sshd[5799]: debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
May 10 22:47:11 home sshd[5799]: Failed none for megahertz from 192.168.1.2 port 59061 ssh2
```

Putty:
```

2012-05-10 22:47:08	Looking up host "192.168.1.10"
2012-05-10 22:47:08	Connecting to 192.168.1.10 port 22
2012-05-10 22:47:08	Server version: SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
2012-05-10 22:47:08	Using SSH protocol version 2
2012-05-10 22:47:08	We claim version: SSH-2.0-PuTTY_Snapshot_2011_07_13:r9206
2012-05-10 22:47:08	Doing Diffie-Hellman group exchange
2012-05-10 22:47:08	Doing Diffie-Hellman key exchange with hash SHA-256
2012-05-10 22:47:08	Host key fingerprint is:
2012-05-10 22:47:08	ssh-rsa 2048 ************************
2012-05-10 22:47:08	Initialised AES-256 SDCTR client->server encryption
2012-05-10 22:47:08	Initialised HMAC-SHA1 client->server MAC algorithm
2012-05-10 22:47:08	Initialised AES-256 SDCTR server->client encryption
2012-05-10 22:47:08	Initialised HMAC-SHA1 server->client MAC algorithm
2012-05-10 22:47:13	Sent password
2012-05-10 22:49:08	Server unexpectedly closed network connection
```

---

### Post by gaurang171 on 2012-05-12
Now i am able to connect.

It was again surprise for me. 
SSH started working the same way it stopped. means. all of a sudden i found that SSH is not working and after 3-4 days again all of a sudden i found that its working. 
Now i dont know what did i do wrong? no settings changed. nothing done dusing these days and its started .

---

### Post by mexys on 2012-05-13
> **gaurang171 said:**
> Now i am able to connect.

It was again surprise for me. 
SSH started working the same way it stopped. means. all of a sudden i found that SSH is not working and after 3-4 days again all of a sudden i found that its working. 
Now i dont know what did i do wrong? no settings changed. nothing done dusing these days and its started .
Me too. Since last night it worked as before without any config changes.

---

