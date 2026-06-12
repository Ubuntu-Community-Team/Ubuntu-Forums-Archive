---
title: "SSH Tunnel does not work"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by DrGigabit on 2012-04-02
Hello,

I have a very strange issue with SSH. I have an Ubuntu Server installed in a local network. Its hostname, say **ams.main.local**

I have this machine published using Microsoft Forefront TMG by using different public name. Say, **public.mydomain.com**

ams.main.local ---> TMG (public.mydomain.local) <--- client 

I want to connect to that machine using public key from my client (MacOS). I followed this guide:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
basically did everything required to set up public key auth.

However I am not able to access the machine. I guess that's because the public name and internal host names do not match.

Here is the log file I am getting

ssh -vvv [email]andrei@public.mydomain.com[/email]
OpenSSH_5.9p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /Users/user/.ssh/config
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to public.mydomain.com [193.203.127.38] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/Users/user/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /Users/user/.ssh/id_rsa type 1
debug1: identity file /Users/user/.ssh/id_rsa-cert type -1
debug1: identity file /Users/user/.ssh/id_dsa type -1
debug1: identity file /Users/user/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: match: OpenSSH_5.8p1 Debian-7ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "public.mydomain.com" from file "/Users/user/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /Users/user/.ssh/known_hosts:22
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 120/256
debug2: bits set: 493/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 36:48:7b:c2:4e:ba:c4:60:81:cd:99:e8:e5:90:17:2c
debug3: load_hostkeys: loading entries for host "public.mydomain.com" from file "/Users/user/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /Users/user/.ssh/known_hosts:22
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "193.203.127.38" from file "/Users/user/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /Users/varanovich/.ssh/known_hosts:16
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'public.mydomain.com' is known and matches the RSA host key.
debug1: Found key in /Users/user/.ssh/known_hosts:22
debug2: bits set: 529/1024
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
debug2: key: /Users/user/.ssh/id_rsa (0x7ffb11c1bb10)
debug2: key: /Users/user/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/user/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/user/.ssh/id_dsa
**debug3: no such identity: /Users/user/.ssh/id_dsa**
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password


I marked this line in bold: debug3: no such identity: /Users/user/.ssh/id_dsa
Seems to be an issue with the identity mapping, I guess that's because the differences in public and internal host names?

Any help is appreciated.

Thanks,
Andrei

---

### Post by papibe on 2012-04-02
Hi DrGigabit. Welcome to the forums!

First I would like check the file permissions on your client. Could you post the result of this command?
```
ls -la .ssh
```
Regards.

---

### Post by DrGigabit on 2012-04-02
Here we go (this is from the client)

```
drwx------   7 user  staff   238 Apr  2 21:04 .
drwxr-xr-x+ 96 user  staff  3264 Apr  2 21:04 ..
-rw-r--r--   1 user  staff   104 Mar 26 17:57 config
-rw-------   1 user  staff  1679 Aug  6  2011 id_rsa
-rwx------   1 user  staff   429 Aug  6  2011 id_rsa.pub
-rw-r--r--   1 user  staff  9163 Apr  2 16:15 known_hosts
```

---

### Post by papibe on 2012-04-02
> **DrGigabit said:**
> 
ebug3: Incorrect RSA1 identifier
debug3: Could not load "/Users/user/.ssh/id_rsa" as a RSA1 public key


> **DrGigabit said:**
> ```
-rw-------   1 user  staff  1679 Aug  6  2011 id_rsa
-rwx------   1 user  staff   429 Aug  6  2011 id_rsa.pub
-rw-r--r--   1 user  staff  9163 Apr  2 16:15 known_hosts
```

It looks you have a corrupted key, or a key type mismatch.

We can continue debuging it, but at this point it would be easier to do again the process of creating new keys. If you decide to go in that direction, start by removing your current keys (make sure login using passwords is enabled on the server):
```
rm -rf .shh/id*
```
Hope that helps, and tell us how it goes.
Regards.

---

