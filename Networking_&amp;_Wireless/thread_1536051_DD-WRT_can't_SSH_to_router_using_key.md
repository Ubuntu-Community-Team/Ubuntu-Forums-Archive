---
title: "DD-WRT can't SSH to router using key"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by wannabegeek on 2010-07-21
good day

I've been trying to setup my wireless router, WGR54GL using DD-WRT .
I have enabled SSHd and set to no password.
I generated a key pair and added them to keyring and see them in my .ssh dir ,
and set the port to listen on 117... cut and paste the public key into the GUI for DD-WRT and was careful to follow the format on [http://www.ddwrt.com/wiki/index.php/Telnet/SSH_and_the_Command_Line#Setting_Up]("http://www.dd-wrt.com/wiki/index.php/Telnet/SSH_and_the_Command_Line#Setting_Up")

lost for now...
thank you
wbg

**UPDATE:**
enabled password and was successful logging in as root and can cd to .ssh and see my pub key in 'authorized_keys'

[PHP]
daniel@Geek:~/.ssh$ ssh -p 117 -v 10.0.0.1
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.0.0.1 [10.0.0.1] port 117.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug1: identity file /home/daniel/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/daniel/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.51
debug1: no match: dropbear_0.51
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host '[10.0.0.1]:117' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:10
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
DD-WRT v24 mini (c) 2008 NewMedia-NET GmbH
Release: 07/27/08 (SVN revision: 10011)
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/daniel/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/daniel/.ssh/identity
debug1: Trying private key: /home/daniel/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
[/PHP]

---

