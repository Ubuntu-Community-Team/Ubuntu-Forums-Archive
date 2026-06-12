---
title: "Sshd Segmentation Fault on Ubuntu 9.04"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Sputnik82 on 2009-05-04
Hi
I've been using my computer as a ssh server for several months and since I updated to Ubuntu 9.04 it stoped working. Do you think it may have any relation with the segmentation falut seen on the server log?
Thank you for your help

_Server /var/log/syslog_
> 
May  4 12:07:03 laptop kernel: [ 8344.704115] sshd[9287]: segfault at 708421f8 ip b7b33170 sp b70c8fa4 error 6 in libc-2.9.so[b7ac1000+15c000]


_Client Output_
> 
sputnik@laptop:~$ ssh -v IP
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to IP [IP] port 22.
debug1: Connection established.
debug1: identity file /home/sputnik/.ssh/identity type -1
debug1: identity file /home/sputnik/.ssh/id_rsa type -1
debug1: identity file /home/sputnik/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
The authenticity of host 'IP (IP)' can't be established.
RSA key fingerprint is 04:51:ea:6d:b5:ec:d3:0e:eb:ce:cf:a1:d0:17:fa:de.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'IP' (RSA) to the list of known hosts.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/sputnik/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/sputnik/.ssh/identity
debug1: Trying private key: /home/sputnik/.ssh/id_rsa
debug1: Trying private key: /home/sputnik/.ssh/id_dsa
debug1: Next authentication method: password
sputnik@IP's password: 
Connection closed by IP
sputnik@laptop:~$ 


---

