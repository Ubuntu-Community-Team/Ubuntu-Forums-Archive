---
title: "SSH or vodafone huawei E272 or anything else?"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by junkfer on 2009-02-12
Hi!

Today i meet with the following situation. i have a asus note with intrepid.

From home, behind a linksys wrt54gl router, many time,  i log in with ssh to a solaris server, who is on one ISP serverfarm. I could log in to a server who is at home too (this server is also a solaris). I could the ssh session leave for any time, when i go back the session is live, i could work.

Today i bring my laptop with me to working.I think i can work today with my Voda Huawei E272 modem.

My experiences in this architecture:
- i can log in via ssh to my router, the session is live everytime. Without any "error" or "notice" in "ssh -v" like the follow.
- if i probe log in to anyone of the mentioned servers the shell is opened i can work, but after few seconds (10-max 20) closed with the following message:

 Read from remote host xxxxxx.xxxxxxxx.hu: Connection reset by peer
Connection to "host" closed.

in ssh -v i can see the following:

debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

I read after, and i probed the following to do :

in local sshd_config set "GSSAPIAuthentication=no", so would the connection time a bit faster, but the connection where closed.

Everyone who could me help? RTFM what? Thanks for any help....

---

### Post by junkfer on 2009-02-12
Sorry guys, i forgott a thing , and this gived me the solution.
That is how the Voda modem working, in compressed or in standard mode.
My modem was in compressed mode, and this "loved" the ssh not.

---

