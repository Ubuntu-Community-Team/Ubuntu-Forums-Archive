---
title: "ssh timed out while waiting to read"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by alenis on 2009-08-10
I have a server at work allowing SSH connections. I was able to connect from home with Hardy, but since I switched to Jaunty when I try:

[HTML]ssh myname@office[/HTML]

I get 

[HTML]Connection to xxx.xxx.xxx.xxx timed out while waiting to read[/HTML]

Nothing has changed on the server. I have another computer at the office, with Hardy, from which I can still establish an ssh connection to the server.

I noticed that Jaunty has a newer version of ssh (5.1p1 vs 4.7p1) so probably this is the cause of the problem. 
Should I downgrade ssh or is there another solution?

----
This is the output of ssh with the -v option

[HTML]
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/myname/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ufficio [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/myname/.ssh/identity type -1
debug1: identity file /home/myname/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/myname/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*
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
debug1: Host 'ufficio' is known and matches the RSA host key.
debug1: Found key in /home/myname/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Connection to 217.133.134.26 timed out while waiting to read
[/HTML]



----
Should I downgrade, how to do it? If I try to remove the current version of openssh, synaptic says I should remove also ubuntu-desktop...

---

### Post by Shorin on 2010-09-23
[http://ubuntuforums.org/showthread.php?p=9880179#post9880179](http://ubuntuforums.org/showthread.php?p=9880179#post9880179) worked for me.

---

### Post by alenis on 2010-10-05
Thanks!

---

