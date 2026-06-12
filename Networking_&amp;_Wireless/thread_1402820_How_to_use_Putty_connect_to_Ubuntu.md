---
title: "How to use Putty connect to Ubuntu?"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by Kobold3012 on 2010-02-09
I have 2 computer: 1 computer install ubuntu v9.10, in this computer already installed openssh-server and openssh-client, and 1 computer install windows. In computer with windows , i used putty connect to computer with ubuntu, but i can't connect. I don't understand what's error.
In the Putty , i configured: 
IP : IP address of computer Ubuntu.
Port 22
Connection Type SSH

This is error: "Network Error: Software caused connection abort"

In computer with windows, i can ping computer with ubuntu and in computer with ubuntu i can ping computer with windows.

---

### Post by pirateghost on 2010-02-09
did you install openssh-server on the ubuntu box?

---

### Post by Kobold3012 on 2010-02-10
> **pirateghost said:**
> did you install openssh-server on the ubuntu box?

ubuntu box ? I don't understand , but in synaptic i saw openssh-server and openssh-client already installed.
And in terminal i used command : sudo dkpg -s openssh-server and result this package already installed.

Give me idea ! Thanks

---

### Post by Kobold3012 on 2010-02-11
I already checked computer with ubuntu :
- /etc/ssh/sshd_config: in this file port 22, PermitRootLogin yes...

And in this machine installed with openssh-server, and openssh-client. But in this time, this error is maintaining, i don't find idea to fix this error.

---

### Post by suseendran.rengabashyam on 2010-02-11
Hi,

May I know what version of PuTTy are you using ? You can check the version by Right Clicking over PuTTy Icon and then going to Properties->Version.

If you are using an old version(< 0.60.0.0), download the latest version(0.60.0.0) and see whether you get the same error.

Also check if there is Firewall in the picture.

You can refer the following link
[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter10.html#errors-connaborted](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter10.html#errors-connaborted)
for more details regarding this issue.

---

### Post by Kobold3012 on 2010-02-11
Thanks everybody to help me! I solved this my problem, now i can use putty connect to Ubuntu.

---

### Post by fsboreal on 2012-08-20
> **Kobold3012 said:**
> Thanks everybody to help me! I solved this my problem, now i can use putty connect to Ubuntu.

So what was the solution to this?

---

