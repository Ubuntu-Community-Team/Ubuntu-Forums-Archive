---
title: "Cannot ssh: Permission denied (publickey)."
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2013-03-27
I cannot determine why I can't ssh to this other PC in my house. The -v switch doesn't really tell me why I can't connect but maybe there's a clue in here that someone will recognize? The only thing I see that looks odd is "Roaming not allowed by server" but I don't know what that means or how to fix it. I've done some googling and I'm finding a lot of guesses related to things like file permissions but I haven't changed any permissions. The laptop (the IP ending in 9) can ssh just fine to the main PC but the main PC cannot ssh to the laptop. This is also my first time attempting to do so.

scottbomb@main-linux:~$ ssh -v scottbomb@192.168.1.9
OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.9 [192.168.1.9] port 22.
debug1: Connection established.
debug1: identity file /home/scottbomb/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/scottbomb/.ssh/id_rsa-cert type -1
debug1: identity file /home/scottbomb/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/scottbomb/.ssh/id_dsa-cert type -1
debug1: identity file /home/scottbomb/.ssh/id_ecdsa type -1
debug1: identity file /home/scottbomb/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.1p1 Debian-4
debug1: match: OpenSSH_6.1p1 Debian-4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.1p1 Debian-4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 97:06:8a:84:6a:78:96:ae:a1:5b:0a:f6:df:68:1c:72
debug1: Host '192.168.1.9' is known and matches the ECDSA host key.
debug1: Found key in /home/scottbomb/.ssh/known_hosts:7
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering DSA public key: /home/scottbomb/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: Offering RSA public key: /home/scottbomb/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/scottbomb/.ssh/id_ecdsa
debug1: No more authentication methods to try.
Permission denied (publickey).

I then tried ssh-copy-id -v scottbomb@192.168.1.9 and got this mess:

OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
Pseudo-terminal will not be allocated because stdin is not a terminal.
ssh: Could not resolve hostname umask 077; test -d ~/.ssh || mkdir ~/.ssh ; cat >> ~/.ssh/authorized_keys && (test -x /sbin/restorec: No such file or directory
scottbomb@main-linux:~$

---

### Post by prodigy_ on 2013-03-27
Just append the contents of one of your public key files (e.g. **id_dsa.pub**) as a new line to the **/home/scottbomb/.ssh/authorized_keys** file on the server.

For more info: [OpenSSH/Keys HOWTO](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

