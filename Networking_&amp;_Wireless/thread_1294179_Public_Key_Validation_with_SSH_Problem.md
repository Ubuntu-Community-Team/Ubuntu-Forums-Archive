---
title: "Public Key Validation with SSH Problem"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by pteri498 on 2009-10-18
Hello.

I am trying to ssh into my school network with public key validation so I don't need to keep entering a password, and while it worked before, I think they upgraded to Fedora 11 or something and it no longer works.

I started from scratch with a suitable tutorial ([http://ubuntuforums.org/showthread.php?t=30709](http://ubuntuforums.org/showthread.php?t=30709)) and it does not work. I get the following verbose output:

```

ssh -v remoteid@vogon.csc.calpoly.edu
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to vogon.csc.calpoly.edu [129.65.158.6] port 22.
debug1: Connection established.
debug1: identity file /home/pteri/.ssh/identity type -1
debug1: identity file /home/pteri/.ssh/id_rsa type -1
debug1: identity file /home/pteri/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.0
debug1: match: OpenSSH_5.0 pat OpenSSH*
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
debug1: Host 'vogon.csc.calpoly.edu' is known and matches the RSA host key.
debug1: Found key in /home/pteri/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received

debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering public key: /home/pteri/.ssh/id_dsa
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /home/pteri/.ssh/identity
debug1: Trying private key: /home/pteri/.ssh/id_rsa
debug1: Next authentication method: password
pteri@vogon.csc.calpoly.edu's password: 

```

Note that I have successfully logged into my own machine from the school's server, so I believe this computer should be in known_hosts. What else can I do to fix this?

---

