---
title: "Linux Active Directory Integration"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by tiagoskid on 2009-04-08
Hello,

I am trying to setup a unified structure, all systems authenticating in Active Directory, I'm using LDAP and Kerberos. 

I've had some success with the Windows/Linux integration, but for it to work I have to duplicate the usernames list in Linux, but I know it's checking against AD because the passwords are different and I'm using the Windows one.

Can you please tell me what I'm missing??

Thankyou.

---

### Post by compiledkernel on 2009-04-08
Community doc here -- [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

Unless your trying to create an LDAP server to backup or clone an existing AD (or replace, some do this too, and that involves quite a bit more work).

---

### Post by tiagoskid on 2009-04-09
Hy,

Thanks, but it didn't awsner my question, I do not want to( can't)  use Samba in this project, and in the first page there is
a note that the users from the AD have to exist in "/etc/passwd", is this mandatory? I already have things running like this, but my goal is to have a unique userlist in the AD.


Thankyou.

---

