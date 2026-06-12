---
title: "SSH: No connection"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by mike_abc on 2010-10-09
Hi everybody,

I try to connect from my laptop to my server on my home network thru SSH.
Both computers are running Ubuntu 10.04 64-bit.

The server has SSH installed and running.

When I issue the ssh -v command I get this:

OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to [...].
debug1: Connection established.
debug1: identity file /home/mike/.ssh/identity type -1
debug1: identity file /home/mike/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/mike/.ssh/id_dsa type -1
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
debug1: Host '[...]' is known and matches the RSA host key.
debug1: Found key in /home/mike/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/mike/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/mike/.ssh/identity
debug1: Trying private key: /home/mike/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

**Question #1:** The <user> on the client does not exist on the server. Is this OK ? 
If it is, what <username>  should my **ssh** command use ?

**Question #2:** ssh seems to try to connect using my DSA private key. I want it to try to connect using my RSA private key. How do I do this ?

**Question #3:** What else should I do to make it work ?

Cheers,
Mike

---

### Post by mike_abc on 2010-10-10
And no reply so far, also ! Any ideas ?!
[B]
[COLOR=Red]Strike[/COLOR] Question #1 ! [/B]In view of what I read in the meantime, the username on the server is the one which matters, since I actually connect as that user on the server.

Mikey

---

### Post by mike_abc on 2010-10-10
OK, so it works now - dunno exactly why :P.

I did the following: 

I recopied the public key to the Host and cat'ed it in authorized_keys ([B]by creating an empty file and then updating it).
[/B]
I changed the authorized_keys2 filename back to **authorized_keys** (as it was in the beginning) and made sure that its correctly referred to in **sshd_config**. (I had changed the name because of some wiseguy's post on the Net.)

I think that's all. Now its working. :guitar:


Cheers mates,

Mike

---

