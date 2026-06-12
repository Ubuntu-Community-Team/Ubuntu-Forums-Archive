---
title: "samba"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by gozila on 2009-08-23
I'm new in ubuntu,how can I add pc with ubuntu9.4 to network(all pc's  in the network are xp and the server is win2003 with AD).. i heard that I have to edit in smb.config but how?!!!!!



domain is arcoma.com

pc with ubuntu 10.2.2.244

server 2003 10.2.2.118

---

### Post by dmizer on 2009-08-23
Try this: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by gozila on 2009-08-24
I really lost.. is there anyone can guide me step by step how configure samba and network printer ? please :)

---

### Post by dmizer on 2009-08-24
> **gozila said:**
> I really lost.. is there anyone can guide me step by step how configure samba and network printer ? please :)

Is there something about the guide you don't understand, or something you need help with? The guide I linked to above shows you step by step how to join AD.

---

### Post by gozila on 2009-08-26
thanks [[COLOR=#D40000]**dmizer**[/COLOR]]("http://ubuntuforums.org/member.php?u=77219")...

but can you explain for me some points, if u dont main :) 


1)what the command to open this file: /etc/samba/smb.conf


2) 
[global]
        security = ads #??
        realm = LAB.EXAMPLE.COM #??
        password server = 10.0.0.1 #??
# note that workgroup is the 'short' domain name
        workgroup = LAB #??
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes #??
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
for my network have i have to change anything from above?


my domain is arcoma.com
pc ubuntu 10.2.2.244
server 2003 10.2.2.118

---

### Post by Visserys on 2009-08-26
Im having issues with this too. 
I've tried a bunch of different work arounds and Im not sure what else to do. Connecting to windows shares was fine in other releases. 
It doesn't work in the latest 9.04 or 9.10 versions.
Im not sure what I should post, but if someone told me what they needed to see, I could find it and post it up here.

Thanks, for any possible help

---

### Post by dmizer on 2009-08-26
> **gozila said:**
> 1)what the command to open this file: /etc/samba/smb.conf
```
gksudo gedit /etc/samba/smb.conf
```


> **gozila said:**
> 2) 
[global]
        security = ads #??
        realm = LAB.EXAMPLE.COM #??
        password server = 10.0.0.1 #??
# note that workgroup is the 'short' domain name
        workgroup = LAB #??
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes #??
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
for my network have i have to change anything from above?

You should ask your server's administrator those questions.

---

### Post by gozila on 2009-08-27
He does not know anything about linux....I meant what is meaning every line??

---

### Post by dmizer on 2009-08-27
> **gozila said:**
> He does not know anything about linux....I meant what is meaning every line??

Even if he knows nothing about Linux, he administrates the network. Therefore, he should be able to tell you what to enter in those lines.

---

