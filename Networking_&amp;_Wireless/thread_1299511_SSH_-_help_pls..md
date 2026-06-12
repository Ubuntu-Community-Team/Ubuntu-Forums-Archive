---
title: "SSH - help pls."
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by NJC on 2009-10-24
I fixed the host key verification error in my [other]("http://ubuntuforums.org/showpost.php?p=8152406&postcount=15") thread. 

But I STILL have to enter a SSH password! Why the "no such identity: /root/.ssh/id_rsa" etc errors?
[URL="http://ubuntuforums.org/showthread.php?t=1139420"]
[/URL] sudo ssh -vvv 192.168.1.101
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.101 [192.168.1.101] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
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
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 129/256
debug2: bits set: 495/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.1.101' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug2: bits set: 515/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /root/.ssh/identity ((nil))
debug2: key: /root/.ssh/id_rsa ((nil))
debug2: key: /root/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug3: no such identity: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug3: no such identity: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

Client:
> :~/.ssh$ ls -l
total 20
-rw------- 1 user  736 2009-10-23 19:02 id_dsa
-rw-r--r-- 1 user  607 2009-10-23 19:02 id_dsa.pub
-rw------- 1 user  1743 2009-10-23 19:13 id_rsa
-rw-r--r-- 1 user  399 2009-10-23 19:13 id_rsa.pub
-rw-r--r-- 1 user  442 2009-10-23 07:24 known_hosts
Server:
>  ls -l ~/.ssh
total 4
-rw------- 1 user 399 2009-10-23 19:13 authorized_keys


From sshd_config on server:> RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys


---

### Post by tzicatl on 2009-10-24
Hi, this is what I do on my computer:

My public key is in: ~/.ssh/johndoe_dsa.ssh with proper permissions. SSH will complain if they are not.

my.server.com has the IP Address: 10.11.12.13

tzicatl@hormiga-blanca:~$ cat .ssh/config
Host my.server.com
    User jhondoe
    Protocol 2
    PubkeyAuthentication yes
    HostbasedAuthentication yes
    IdentityFile ~/.ssh/johndoe_dsa.ssh
Host 10.11.12.13
    User jhondoe
    Protocol 2
    PubkeyAuthentication yes
    HostbasedAuthentication yes
    IdentityFile ~/.ssh/johndoe_dsa.ssh


Just do:
```
ssh my.server.com
```
or
```
ssh 10.11.12.13
```

Write the key passphrase and there you are!

If you want passwordless ssh (which i did once for clustering), just create a private/public pair with no pasphrase.

Regards

---

### Post by NJC on 2009-10-26
It is beyond ridiculous how much time I've spent fiddling with this. Perseverance to the point of idiocy to be sure. I STILL CAN'T GET PUBLIC KEYS TO WORK!

Does this mean anything?

>  ssh -1 -v 192.168.1.101
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Connecting to 192.168.1.101 [192.168.1.101] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
Protocol major versions differ: 1 vs. 2


---

### Post by Lars Noodén on 2009-10-26
Please don't use protocol 1.  Use protocol 2.  

**Preparation** for using public key authentication with SSH:

1) make a key pair, using a good, strong, long passphrase:

[INDENT][FONT="Courier New"]ssh-keygen -b 2048 -t rsa -f njc_rsa[/FONT][/INDENT]


2) put the public key into the file ~/.ssh/authorized_keys in your account on the server you want to log into

[INDENT][FONT="Courier New"]cat njc_rsa.pub >> ~/.ssh/authorized_keys[/FONT][/INDENT]

2b) make sure the permissions are correct on the server account

[INDENT][FONT="Courier New"]chmod 0700 ~/.ssh/
chmod 0600 ~/.ssh/authorized_keys[/FONT][/INDENT]


3) put the public and private key into the directory ~/.ssh/ on the machine you want to log in from

**Login**

Login without key to make sure you can, then log out again.

[INDENT][FONT="Courier New"]ssh -l njc *xx.yy.zz.aa*;
exit;[/FONT][/INDENT]

Now try the key

[INDENT][FONT="Courier New"]ssh -i ~/.ssh/njc_rsa  -l njc *xx.yy.zz.aa*;[/FONT][/INDENT]

where *xx.yy.zz.aa* is the ip address or hostname of the server

---

