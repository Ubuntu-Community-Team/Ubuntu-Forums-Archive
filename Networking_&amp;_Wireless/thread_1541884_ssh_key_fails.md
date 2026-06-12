---
title: "ssh key fails"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by CraigFoote on 2010-07-29
A few days ago something went south on my server and my account disappeared. From safe boot I found the encrypted home folder was still there but grub didn't show my account as a login option. I figured out 'adduser' enough to create the account again and point to that home directory and I am now able to log in and run most stuff fine. SSH login by keys however is still not working. Password login works ok but I really liked the key access.

I emptied the server's ~/.ssh folder, recreated the keys on my laptop, scp'd the public key to the server's ~/.ssh folder and copied it into authorized_keys2. Attempting to access the server from the laptop now tries to use the key then defaults to password. I don't quite know how to interpret the debug output so I could use some help. What am I doing wrong?

craig@notebook:~$ ssh -v server
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server [192.168.1.103] port 22.
debug1: Connection established.
debug1: identity file /home/craig/.ssh/identity type -1
debug1: identity file /home/craig/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/craig/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /home/craig/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/craig/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/craig/.ssh/identity
debug1: Trying private key: /home/craig/.ssh/id_dsa
debug1: Next authentication method: password

---

### Post by marc.verwerft on 2010-07-30
You probably should set maximum logging for the ssh daemon and have a look at that output too.
I don't see anything wrong on the client side.

Regards,

Marc

---

