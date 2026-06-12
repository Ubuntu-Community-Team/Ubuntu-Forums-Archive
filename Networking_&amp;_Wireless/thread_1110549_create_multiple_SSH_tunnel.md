---
title: "create multiple SSH tunnel"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by mmbathan on 2009-03-29
Hi guys,

I have a question about How I can connect between client and server using multiple SSH tunnel from specific port to specific port in the other machine? 

Regards,

---

### Post by dusan.saiko on 2009-03-30
this is what I am using for ssh tunnels. do you mean something like this ?

ssh -Y -C -c blowfish -L 3307:remotecomp1:3306 -L 3308:remotecomp2:3308  [email]user@linux.comp[/email]

remotecomp1 and remotecomp2 are names relative to the "linux.comp" server, if you would use "localhost", it means the remote server itself.

---

### Post by linuxfreak003 on 2013-02-16
That's really cool I didn't know you could use -L more than once. I guess I should have just tried...

---

