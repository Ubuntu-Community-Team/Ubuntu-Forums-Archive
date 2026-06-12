---
title: "SSH session statistics"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by oraerk on 2010-01-04
Is there some way to get ssh session statistics on request, without verbose mode?
After some googling, I've found a guide:
[http://www.thegeekstuff.com/2008/05/5-basic-linux-ssh-client-commands/#more-3](http://www.thegeekstuff.com/2008/05/5-basic-linux-ssh-client-commands/#more-3)

It states, that when given escape char **~** and **s**, the desired statistics are shown:
```
remotehost$  **[Note: The ~s is not visible on the command line when you type.] **
        remote host: remotehost
        local host: localhost
        remote version: SSH-1.99-OpenSSH_3.9p1
        local version:  SSH-2.0-3.2.9.1 SSH Secure Shell (non-commercial)
        compressed bytes in: 1506
        uncompressed bytes in: 1622
        compressed bytes out: 4997
        uncompressed bytes out: 5118
        packets in: 15
        packets out: 24
        rekeys: 0
        Algorithms:
        Chosen key exchange algorithm: diffie-hellman-group1-sha1
        Chosen host key algorithm: ssh-dss
        Common host key algorithms: ssh-dss,ssh-rsa
        Algorithms client to server:
        Cipher: aes128-cbc
        MAC: hmac-sha1
        Compression: zlib
        Algorithms server to client:
        Cipher: aes128-cbc
        MAC: hmac-sha1
        Compression: zlib
        localhost$
```Though i've tried and never succeded. More than that, after giving **~? **sequence, I see only:
```
Supported escape sequences:
  ~.  - terminate connection (and any multiplexed sessions)
  ~B  - send a BREAK to the remote system
  ~C  - open a command line
  ~R  - Request rekey (SSH protocol 2 only)
  ~^Z - suspend ssh
  ~#  - list forwarded connections
  ~&  - background ssh (when waiting for connections to terminate)
  ~?  - this message
  ~~  - send the escape character by typing it twice
(Note that escapes are only recognized immediately after newline.)

```Am I doing something wrong? How can I get the statistics?

---

### Post by diesch on 2010-01-04
OpenSSH doesn't support this. The web page's author uses  the client from *SSH Communications Security *  ("SSH-2.0-3.2.9.1 SSH Secure Shell (non-commercial)")

---

### Post by oraerk on 2010-01-04
My bad. Thanks for the answer.

---

