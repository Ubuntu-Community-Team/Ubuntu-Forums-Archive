---
title: "Really dumb proftpd question?"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by evilbuntu on 2008-12-11
I have a group in ubuntu 8.04 that i set up access to a certain directory in my FTP. i want to let them download (possibly upload) to it but do not want them to be able to delete things. is there a way to set this up.

i found an option to disable overwriting of files but even when i disable that i can still go in under one of their accounts and delete things....

thanks


a second question that was never answered from a different post, just in case someone here might know is; is there a way to set up a vnc account for a freind but only give him privileges to look around but not make changes?

thanks on this one too.

---

### Post by etamax on 2008-12-31
I don't know if I'm late in the answer but can you post your proftpd.conf configuration?

However there is a <Limit> that can do what you want, as described [here](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Limit.html)

```

  <Directory /path/to/dir>
    <Limit DELE>
      AllowUser ftpadm
      DenyAll
    </Limit>
  </Directory>

```


For the question about the VNC, I'm using x11vnc and you try to use it with the 
```
-viewonly
```
command.

Hope these help

Massimo

---

### Post by evilbuntu on 2009-01-14
> **etamax said:**
> I don't know if I'm late in the answer but can you post your proftpd.conf configuration?

However there is a <Limit> that can do what you want, as described [here](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Limit.html)

```

  <Directory /path/to/dir>
    <Limit DELE>
      AllowUser ftpadm
      DenyAll
    </Limit>
  </Directory>

```


For the question about the VNC, I'm using x11vnc and you try to use it with the 
```
-viewonly
```
command.

Hope these help

Massimo

hey man thanks for answering. i have just seen your post. where can i find this proftpd.cfg file to post?

thanks again

---

### Post by etamax on 2009-01-14
> **evilbuntu said:**
> hey man thanks for answering. i have just seen your post. where can i find this proftpd.cfg file to post?

thanks again

You can find it in /etc/proftpd

---

### Post by superprash2003 on 2009-01-14
have you tried gproftpd? GUI for proftpd..

---

