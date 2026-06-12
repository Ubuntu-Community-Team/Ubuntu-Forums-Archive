---
title: "What form of remote connectivity is the best for my school."
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2009-02-02
I know the tech guy at my school and he's actually pretty experienced, i want their samba server to be accessible from my house, i suggested ftp and he says that it is risky and he doesn't want to risk it. I suggested a VPN and he said that it would be too hard to pass out to everyone and there are compatibility issues. I want to be able to access the samba network from home, whats the safest way, yes their servers use linux, they use redhat, debian, and ubuntu. I don't know what one controls which though.

---

### Post by dragos240 on 2009-02-04
Bump

---

### Post by dragos240 on 2009-02-05
Can you hear the echo?

---

### Post by dragos240 on 2009-02-06
pretty quiet in here, can you hear an echo?

---

### Post by da mono on 2009-02-06
whaat about an ssh remote session ??? have you told him that, i use webmin for that but it should we a similar program for just exploring samba

---

### Post by dragos240 on 2009-02-06
> **da mono said:**
> whaat about an ssh remote session ??? have you told him that, i use webmin for that but it should we a similar program for just exploring samba

Secure shell? Hmm, that could work. I'll think about it.

---

### Post by mtopro on 2009-02-06
Agreed.  SSH can be pretty simple to setup, and is very secure providing encrypted connection between your computer and the server.  You can also use the browsers you are accustomed to, through SFTP.

---

### Post by dragos240 on 2009-02-06
> **mtopro said:**
> Agreed.  SSH can be pretty simple to setup, and is very secure providing encrypted connection between your computer and the server.  You can also use the browsers you are accustomed to, through SFTP.

He's worried about hackers, would it be secure to that?

---

### Post by ieee488 on 2009-02-07
**nothing is 100% secure**.

You need a network admin who knows what he/she is doing. Otherwise, your server and network is vulnerable.

If I were him, I wouldn't be doing something like this on the side without authorization from his superiors. He can lose his job over this.

---

### Post by mtopro on 2009-02-08
It is true that the person setting it up needs to research how to do it correctly, and you will need the support of your network admin.

The encryption can be far superior than what your bank uses with HTTPS or SSL 128/256 bit encryption.

It is really pretty simple to setup. Please start with this excellent tutorial:  [http://suso.org/docs/shell/ssh.sdf]("http://suso.org/docs/shell/ssh.sdf") 

hth

---

