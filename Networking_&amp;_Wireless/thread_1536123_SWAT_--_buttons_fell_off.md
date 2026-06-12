---
title: "SWAT -- buttons fell off?"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by drjoeross on 2010-07-21
Greetings,
   I am trying to use SWAT to better configure  Samba.conf  I have swat installed and working but it is missing the GLOBAL button which is its main configuration tool?
   Can anyone tell me why?  See image of my SWAT in a browser attached to this text. 
Thanks,
Joe:)

---

### Post by Marcelo Ruiz on 2010-08-16
Open System -> Administration -> Users & Groups
click on manage groups
select root
be sure your user name is selected in the list of users

---

### Post by Marcelo Ruiz on 2010-08-16
Also, be sure your /etc/samba/smb.conf has the following permissions:
rwxrwxr--
or
774

---

### Post by vkrische on 2011-09-07
I am completely new to Ubuntu and was having the same problem of only a few buttons showing up in SWAT. After a bit of searching I found an answer. 

I had to set my root password:

```
<snip>
```

Then press alt+F2 and enter [http://localhost:901](http://localhost:901) You can also type that into any browser.

When prompted I logged on with "root" and the password I set.

Maybe setting the root password is something that Linuxers do right away, but I never remember being prompted to set it during the installation. 

The more you know...

---

### Post by raydar on 2011-11-21
That did the trick for me too, trying to get file sharing back after a Lubunu 11.10 fresh install. Thanks!

---

