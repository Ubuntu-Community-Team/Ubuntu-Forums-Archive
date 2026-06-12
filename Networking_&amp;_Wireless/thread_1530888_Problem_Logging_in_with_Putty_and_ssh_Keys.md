---
title: "Problem Logging in with Putty and ssh Keys"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by igb on 2010-07-14
I need to be able to log into my Ubuntu server from a computer running Windows. I have set my server to disable password based authentication. I can login fine from any Unix computer using ssh key authentication.

If I enable password based authentication I can log in with Putty.

I have generated ssh keys using both puttygen and ssh on my Ubuntu server. I have appended my public key to ~/.ssh/authorized_keys. I have specified which private key to use in Putty. Using either the puttgen key or the Ubuntu key I get "Server unexpectedly closed network connection."

Looking in auth.log all I get is:

```
Jul 14 13:32:16 wilkesley sshd[3975]: refused connect from 217.146.125.41 (217.146.125.41)
```

Anyone any ideas?

Ian.

---

