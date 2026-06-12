---
title: "ssh problem"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by den_elze on 2009-01-27
Hi,

I'm facing the following problem, any help is appreciated

when I do "ssh localhost" on my server I succeed in making a connection BUT when I do ssh on the public ip address on this server, I get 

koen@ubuntu:~$ ssh 62.88.32.144
koen@62.88.32.144's password: 
Permission denied, please try again.
koen@62.88.32.144's password: 
Permission denied, please try again.
koen@62.88.32.144's password: 
Permission denied (publickey,password).


I'm 100% sure the password is correct!
I used the ubuntu tool to check if the ports of my public ip adress are open and port 22 and 23 are open

can someone help...

thanks

---

### Post by update_manager on 2009-01-27
> **den_elze said:**
> Hi,

I'm facing the following problem, any help is appreciated

when I do "ssh localhost" on my server I succeed in making a connection BUT when I do ssh on the public ip address on this server, I get 

koen@ubuntu:~$ ssh 62.88.32.144
koen@62.88.32.144's password: 
Permission denied, please try again.
koen@62.88.32.144's password: 
Permission denied, please try again.
koen@62.88.32.144's password: 
Permission denied (publickey,password).


I'm 100% sure the password is correct!
I used the ubuntu tool to check if the ports of my public ip adress are open and port 22 and 23 are open

can someone help...

thanks

Try 
ssh -l <user> <ip>

---

### Post by den_elze on 2009-01-28
thanks update_manager,

but it gives me the same error :(

---

### Post by bgerlich on 2009-01-28
Start ssh with -vvv (verbose mode) and post the output

---

### Post by den_elze on 2009-01-28
this is the output

koen@ubuntu:~$ ssh -vvv 62.88.32.144
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug2: ssh_connect: needpriv 0
debug1: Connecting to 62.88.32.144 [62.88.32.144] port 22.
debug1: Connection established.
debug1: identity file /home/koen/.ssh/identity type -1
debug1: identity file /home/koen/.ssh/id_rsa type -1
debug1: identity file /home/koen/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.46
debug1: no match: dropbear_0.46
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
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
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug2: dh_gen_key: priv key bits set: 188/384
debug2: bits set: 515/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug3: check_host_in_hostfile: filename /home/koen/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host '62.88.32.144' is known and matches the RSA host key.
debug1: Found key in /home/koen/.ssh/known_hosts:2
debug2: bits set: 525/1024
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
debug2: key: /home/koen/.ssh/identity ((nil))
debug2: key: /home/koen/.ssh/id_rsa ((nil))
debug2: key: /home/koen/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/koen/.ssh/identity
debug3: no such identity: /home/koen/.ssh/identity
debug1: Trying private key: /home/koen/.ssh/id_rsa
debug3: no such identity: /home/koen/.ssh/id_rsa
debug1: Trying private key: /home/koen/.ssh/id_dsa
debug3: no such identity: /home/koen/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
koen@62.88.32.144's password: 
debug3: packet_send2: adding 56 (len 61 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
koen@62.88.32.144's password: 
debug3: packet_send2: adding 64 (len 55 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
koen@62.88.32.144's password: 
debug3: packet_send2: adding 64 (len 55 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).
koen@ubuntu:~$

---

### Post by den_elze on 2009-02-02
anyone an idea how to solve?

---

### Post by leechy9 on 2009-02-04
i just encountered the same issue over here. i forwarded the ports and am able to connect, it just says publickey,password check failed. I even tried to give them a public key to share and it still gives the same issue

---

