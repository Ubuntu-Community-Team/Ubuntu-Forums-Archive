---
title: "sshd connection issues"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by eidanch on 2009-09-10
I am having troubles using the sshd server on my machine (behind a router). I run the server and I can connect with "localhost" or my internal ip address, but if i try to connect from my external ip address it simply doesn't work. I tried opening ports, triggering ports, switching ports, disabling firewall, sshing from another computer, going to windows, using and SSH server there and putty to access it (didn't work).
So I need help running it. If any of you have an idea, share it. 

Thank you
E.C.

and of course, look at the terminal view of the SSH login:

# ssh -v 77.125.87.10
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 77.125.87.10 [77.125.87.10] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.36
debug1: no match: dropbear_0.36
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client 3des-cbc hmac-md5 none
debug1: kex: client->server 3des-cbc hmac-md5 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
Read from socket failed: Connection reset by peer

---

