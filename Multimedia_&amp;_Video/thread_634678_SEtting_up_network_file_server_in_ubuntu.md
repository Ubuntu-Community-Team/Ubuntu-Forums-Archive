---
title: "SEtting up network file server in ubuntu"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-12-08
Hi,

Can someone please recommend a network file server for ubuntu server and client?

i.e. I want a client can access the network file server as if it is accessing a local file.

Thank you.

---

### Post by jpkotta on 2007-12-08
Your best bet is probably samba (server) and cifs (client).  I use swat to configure my samba server.

If you want something quick and dirty, sshfs is really easy.  All you need to do is set up an ssh server on the server and install sshfs on the client.
```
sshfs user@remote:/remote/path /local/path
```

---

### Post by Jose Catre-Vandis on 2007-12-08
I would recommend nfs if you are only running linux/ubuntu. Solid as a rock and transparent once setup.
(although you can setup XP/Vista to access nfs shares)

See here for how to setup on server and client

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

