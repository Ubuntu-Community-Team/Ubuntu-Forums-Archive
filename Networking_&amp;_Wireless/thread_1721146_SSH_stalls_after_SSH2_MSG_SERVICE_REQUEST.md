---
title: "SSH stalls after SSH2_MSG_SERVICE_REQUEST"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by unts on 2011-04-04
I'm trying to ssh to a Digi PortServer TS 16. It stalls and times out (after the default ServerAliveInterval-timeout) on
```
debug1: SSH2_MSG_SERVICE_REQUEST sent
```
[LIST]
[*] This is reproducable on all Ubuntu machines I've tried (a few of them now) running 10.04 and 10.10.
[/LIST]

[LIST]
[*] It works fine on Ubuntu 9.10, Debian 4, Debian 5 and CentOS 4.4.
[*]The same error occurs on several PortServers.
[/LIST]
 
Here's how it should continue: (output from a debian machine)
```
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
```..and continues to the password prompt.

Heres the output from my Ubuntu 10.10 machine:

```
[~] ssh -vv 192.168.0.5
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/myuser/.ssh/config
debug1: Applying options for *
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: auto-mux: Trying existing master
debug1: Control socket "/tmp/myuser@192.168.0.5:22" does not exist
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.5 [192.168.0.5] port 22.
debug2: fd 3 setting O_NONBLOCK
debug1: fd 3 clearing O_NONBLOCK
debug1: Connection established.
debug1: identity file /home/myuser/.ssh/id_rsa type -1
debug1: identity file /home/myuser/.ssh/id_rsa-cert type -1
debug1: identity file /home/myuser/.ssh/id_dsa type -1
debug1: identity file /home/myuser/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version SSH_2.0
debug1: no match: SSH_2.0
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
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
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,cast128-cbc,arcfour
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,cast128-cbc,arcfour
debug2: kex_parse_kexinit: hmac-sha1
debug2: kex_parse_kexinit: hmac-sha1
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-sha1
debug1: kex: server->client aes128-cbc hmac-sha1 none
debug2: mac_setup: found hmac-sha1
debug1: kex: client->server aes128-cbc hmac-sha1 none
debug2: dh_gen_key: priv key bits set: 165/320
debug2: bits set: 516/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host '192.168.0.5' is known and matches the DSA host key.
debug1: Found key in /home/myuser/.ssh/known_hosts:963
debug2: bits set: 538/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
Connection to 192.168.0.5 timed out while waiting to read
```So does anyone know what the problem might be here? Is it a bug or am I just not getting it?

---

### Post by repllccax on 2011-05-13
the problem is: digiport does not support ssh versions above openssh 4.3, and this is a known problem!

have to wait for firmware updates :-(

---

