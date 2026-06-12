---
title: "Can't connect to new ssh server on Ubuntu 12.04"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by Azyx on 2013-03-04
Have just installed ssh (server and client) on a Ubuntu 12.04 64bit system and i got this message when I try to connect from a computer on the local network with:

```
ssh Azyx@192.168.0.4
```

And get this resuls:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
---removed by secutity reason ---
Please contact your system administrator.
Add correct host key in /home/Azyx/.ssh/known_hosts to get rid of this message.
Offending key in /home/Azyx/.ssh/known_hosts:2
RSA host key for 192.168.0.4 has changed and you have requested strict checking.
Host key verification failed.
```

A I remember it, so did I before get another message, with a warning first time I tried to connect. If the message came you could remove the ~/.ssh/known_hosts or remove the line with the change computer and also according to some post here.

I have remove ~/.ssh

Bt It does not help :(. Are there any new security policy in later Ubuntu dists?

How can I add fingerprint RSA shown in this message? Tried to just and the "---removed by secutity reason ---" to known_hosts

/Cheers

---

### Post by Azyx on 2013-03-07
I am sorry! I was stupid to just erase the ~/.ssh/known_hosts on the server, not the client. I'm really sorry, and the only defend I have is that Ubuntu works so well, that I don't need to think about computers ;)

/Cheers

---

### Post by Azyx on 2013-03-07
Can't find how I tag the tread at SOLVED? Is not under Tread tools any more :(

---

