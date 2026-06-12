---
title: "ssh will not accept password"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by roboa1983 on 2011-01-31
Hello,
I'm trying to ssh remotely into my machine. I installed openssh-server and openssh-client, but I'm getting a strange error, where my password is not allowed. I looked at an old forum post
[http://ubuntuforums.org/archive/index.php/t-298504.html]("http://ubuntuforums.org/archive/index.php/t-298504.html"), but none of the solutions seem to work.
Has anybody stumbled upon this after a fresh installation of ubuntu 10.10?

Thanks!

---

### Post by Iowan on 2011-01-31
Just to clarify - when you:```
ssh computername
```it replies (something like):
```
username@computername's password:
```
... then won't accept the password you enter?

---

### Post by matt_symes on 2011-01-31
Hi

What exactly is the error message ?

Kind regards

---

### Post by roboa1983 on 2011-01-31
Iowan, Matt_Symes:

Thanks for the reply. Yes, that's the weird part of the error. I can login perfectly, and I thought I had all the necessary packages, but I try to login, and then get:


 Permission denied (publickey,gssapi-with-mic,password).


after three tries. It is not a password problem either, since sudo works fine.

---

### Post by matt_symes on 2011-01-31
Hi

Have a look at this. Hopefully it will help.

[http://linuxtoolkit.blogspot.com/2010/02/ssh-error-permission-denied.html](http://linuxtoolkit.blogspot.com/2010/02/ssh-error-permission-denied.html)

Kind regards

---

### Post by lisati on 2011-01-31
> **roboa1983 said:**
> 
after three tries. It is not a password problem either, since sudo works fine.

Are you referring to sudo on the machine you are connecting **from**, or on the machine you are connecting **to**? If you're logged in as user1 on *desktop*, and connecting as user2 on *server*, you need to use user1's password for sudo on *desktop*, and user2's password on *server* when asked.

---

### Post by roboa1983 on 2011-01-31
Matt_symes:
Thanks, I'll check that first thing in the morning. 

lisati, I mean the password at the server machine. I can sudo and use the password on the server. The only thing I cannot do right now is ssh from the desktop.

---

### Post by camogli on 2011-02-01
Hi Matt_symes,

I have the same problem as roboa1983 and tried doing what you suggested but that didn't fix it,

best

---

### Post by matt_symes on 2011-02-01
Hi

It might be worth posting the whole text displayed when you log on and not just the last error message (using verbose mode in ssh. the -v switch). 

Please use code tags as the output may be quite large. The code tag is the # in the toolbar above where you type the text.

Kind regards

---

