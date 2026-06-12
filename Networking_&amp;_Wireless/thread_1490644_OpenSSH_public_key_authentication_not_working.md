---
title: "OpenSSH public key authentication not working"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by JVo on 2010-05-22
Hi there. I'm trying to get OpenSSH public key authentication to work. My server runs ubuntu. My client is a windows machine, and I'm using cygwin. 

I tried using the instructions here: [http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

If I test it out using this line:
ssh -v -v -v -o PreferredAuthentications=publickey server.example.org

I get this:
debug3: no such identity: /home/Julie/.ssh/identity
[B]debug1: Offering public key: /home/Julie/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug3: Wrote 368 bytes for a total of 1477[/B]
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/Julie/.ssh/id_dsa
debug3: no such identity: /home/Julie/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).

This is just an excerpt, so if you want the entire output, I can give that.

On the server side, the file /var/log/auth.log says:
May 22 11:33:32 jimthompson sshd[22156]: Invalid user Julie from 10.0.1.3
May 22 11:33:32 jimthompson sshd[22156]: Failed none for invalid user Julie from
 10.0.1.3 port 57919 ssh2

So, how do I make "Julie" a valid user? Thanks!

---

### Post by JVo on 2010-05-22
Update:

Since my user name on the server is julievogelman and on the client: Julie, I decided to try this instead:

$ ssh -v -v -v -o PreferredAuthentications=publickey julievogelman@10.0.1.4

I also added "AllowUsers julievogelman" to /etc/ssh/sshd_config, and then restarted ssh.

I still get the same error on the client. On the server, the auth.log file says:
 Authentication refused: bad ownership or modes for directory /home/julievogelman

Any ideas?

---

### Post by JVo on 2010-05-22
Hmm..okay, nevermind. I actually was able to look up that error and discovered that it was a problem with my directory/file permissions being too loose.

---

