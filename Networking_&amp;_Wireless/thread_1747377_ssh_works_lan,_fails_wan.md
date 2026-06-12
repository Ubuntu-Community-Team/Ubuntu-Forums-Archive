---
title: "ssh works lan, fails wan"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2011-05-02
I can ssh into my server just fine when I'm on the lan.


Here the lan

```


RJMac:~ robbiejo$ ssh -v server@10.10.10.2
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to 10.10.10.2 [10.10.10.2] port 22.
debug1: Connection established.
debug1: identity file /Users/robbiejo/.ssh/identity type -1
debug1: identity file /Users/robbiejo/.ssh/id_rsa type -1
debug1: identity file /Users/robbiejo/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
[COLOR="Red"]debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
Configuration file does not specify default realm[/COLOR]  
###not sure what this is

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '10.10.10.2' is known and matches the RSA host key.
debug1: Found key in /Users/robbiejo/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/robbiejo/.ssh/identity
debug1: Trying private key: /Users/robbiejo/.ssh/id_rsa
debug1: Trying private key: /Users/robbiejo/.ssh/id_dsa
debug1: Next authentication method: password
server@10.10.10.2's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
Linux hyrule 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!



```


When I try to connect from the internet

```



RJMac:~ robbiejo$ ssh -v server@xxx.dyndns.org
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to xxxx.dyndns.org [] port 22.
debug1: Connection established.
debug1: identity file /Users/robbiejo/.ssh/identity type -1
debug1: identity file /Users/robbiejo/.ssh/id_rsa type -1
debug1: identity file /Users/robbiejo/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host



```

I'm using password as my auth not rsa keys.
I have tried deleting the listed files on the client, but not on the server.

---

### Post by wlraider70 on 2011-05-03
shameless bump

---

### Post by wlraider70 on 2011-05-05
the issue was resolved by deleting "known_hosts" in ~/.ssh

I'm not sure what caused it.

---

