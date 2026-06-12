---
title: "Can't connect ssh"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-09-19
Hi, in regular Ubuntu I had no trouble getting ssh to work. I made sure that the required software was installed and from memory it just seemed to work. Now in Kubuntu and I get a message that I've never seen before. 

the message I'm getting is;
> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
3d:60:34:05:f7:0b:4c:6e:08:3f:f1:21:0e:bc:49:1a.
Please contact your system administrator.
Add correct host key in /home/jonny/.ssh/known_hosts to get rid of this message.
Offending key in /home/jonny/.ssh/known_hosts:1
RSA host key for 192.168.1.64 has changed and you have requested strict checking.
Host key verification failed.


What does this mean that I have to do to get it going?

---

### Post by SeijiSensei on 2010-09-19
More than likely you rebuilt 192.168.1.64 recently so it created a new "host key."  When you next connect to the machine, the ssh client will complain because that new key doesn't match the one it has in known_hosts.  Just delete the line in known_hosts (line 1 in your case it reports) and try connecting again.  ssh will now ask whether you want to accept the key for that host; say yes, and off you go.

---

### Post by Jonny87 on 2010-09-19
Thanks, that did the trick. I though it would have been something simple like that.
Thanks.

---

