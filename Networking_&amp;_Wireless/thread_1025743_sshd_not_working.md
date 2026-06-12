---
title: "sshd not working"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by nandonachi on 2008-12-30
have ubuntu 8.10

ive installed the openssh-server from a .deb package an installed it successfully, but when i type sshd -p 2000 in terminal, i get an error as:

"sshd re-exec requires execution with an absolute path"

pls help, and just the basics to start the service,

thanks in advance and a HAPPY NEW YEAR TO EVERYONE

---

### Post by jpkotta on 2008-12-31
Start it with ```
/etc/init.d/ssh start
```
Run without the "start" to see other possibilities.
To specify a port, edit /etc/ssh/sshd_config.

---

### Post by terminator14 on 2009-01-03
Hey. I've been working on setting up my own ssh for the past few days - maybe I can help out. What I do is run
```

$ sudo apt-get install ssh

```
to have it installed. Don't need to download any .deb packages, but the way you did it should be configured the same way. If you want to change the port edit sshd_config like jpkotta mentioned by running 

```
$ sudo gedit /etc/ssh/sshd_config
```

After you are done configuring the sshd_config file you have to restart sshd with 

```
$ sudo /etc/init.d/ssh restart 
```

for the changes to take effect.

---

