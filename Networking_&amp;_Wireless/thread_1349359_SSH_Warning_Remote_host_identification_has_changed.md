---
title: "SSH Warning: Remote host identification has changed!"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by laeg_ on 2009-12-08
Hello, I reinstalled 9.10 on my / partition keeping my /home partition intact. Subsequently I reinstalled ssh and openssh-server but I receive this error when attempting to ssh to myself:

```
laeg@skyrocket:~$ ssh -D 127.0.0.1:5555 laeg@my.visible.remote.ip
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
hex:hex:hex:hex:hex:hex:hex:hex:hex:hex:hex:hex:hex:hex:hex:hex.
Please contact your system administrator.
Add correct host key in /home/laeg/.ssh/known_hosts to get rid of this message.
Offending key in /home/laeg/.ssh/known_hosts:2
RSA host key for my.visible.remote.ie has changed and you have requested strict checking.
Host key verification failed.
```

How can I remedy this? Also, I was planning to ssh using putty from a windows box later this evening, will it be affected?

---

### Post by Lars Noodén on 2009-12-08
> **laeg_ said:**
> Hello, I reinstalled 9.10 on my / partition keeping my /home partition intact. Subsequently I reinstalled ssh and openssh-server ...
How can I remedy this? Also, I was planning to ssh using putty from a windows box later this evening, will it be affected?

In cases where the key has changed contact the system administrator (that's you in this case) and verify the key.  While sitting at the console for the server:

```

# get the fingerprint for the RSA key
ssh-keygen -lf /etc/ssh/ssh_host_rsa_key
xxxx x:x:x:x:x:x:x:x:x:x:x:x:x:x:x:x /etc/ssh/ssh_host_rsa_key.pub (RSA)

# get the fingerprint for the DSA key
ssh-keygen -lf /etc/ssh/ssh_host_dsa_key
1024 x:x:x:x:x:x:x:x:x:x:x:x:x:x:x:x /etc/ssh/ssh_host_dsa_key.pub (DSA)

```

Then go over to the client machine where you got the error and remove the old key from ~/.ssh/known_hosts:

```

ssh-keygen -R my.visible.remote.ip

```

Then try logging in, but only enter the password if and only if the key fingerprint matches what you got on the server console.

---

### Post by laeg_ on 2009-12-08
Thanks for the reply.

I'm sorry, do I replace xxxxxxxxxxxxxxxx (colons between each of them, can't seem to post without making smiley faces...)  with the hex I removed from my post earlier or just as you typed it? Also, if relevant the server and client are the same machine. I mainly use it for logging into from work with PuTTY.

I do at least know to replace my.visible.remote.ip with the actual IP :)

---

### Post by Yoann Juet on 2009-12-08
> **laeg_ said:**
> HSubsequently I reinstalled ssh and openssh-server but I receive this error when attempting to ssh to myself

New RSA or DSA keys have been generated during your reinstallation. That's why you get such a warning.

> Offending key in /home/laeg/.ssh/known_hosts:2

Just edit the file /home/laeg/.ssh/known_hosts, delete the second line then try again to ssh.

---

### Post by Iowan on 2009-12-08
> **laeg_ said:**
>  (colons between each of them, can't seem to post without making smiley faces...)  Wrap CODE tags around it (or disable smilies).

---

### Post by laeg_ on 2009-12-13
Thank you for the assistance.

---

