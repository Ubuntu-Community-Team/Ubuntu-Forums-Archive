---
title: "running xwindows applications over ssh"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by ricardino on 2009-09-14
Hi all, im trying to work out how i could run graphical applications over an ssh session. Ive changed the config settings in my ssh_config and sshd_config files, however, when i try to open any program over ssh, i get the message : 

Warning: environment variable DISPLAY is not set

How would i enable graphical applications over an ssh connection?

Any help would be appreciated.

cheers

---

### Post by uncle-c on 2009-09-14
I assume that you have configured the ssh/d config files to forward X11. Are you logging into the ssh server with the -X option i.e.
```


$ ssh -X user@sshserver.com


```

When looged into the ssh server what is your $DISPLAY variable set to :
```


user@SSHSERVER-$ echo $DSIPLAY


```

---

### Post by ricardino on 2009-09-14
ahh i hadnt read the bit about the -x. Thanks for the help.

---

### Post by i.r.id10t on 2009-09-14
Remember it is -X and not -x 

Personally I use -CY - compress data and forward.  You also need a running X server on your local machine - Linux of course, or cygwin-x or similar for win32.  OS X also has an X server ...

---

