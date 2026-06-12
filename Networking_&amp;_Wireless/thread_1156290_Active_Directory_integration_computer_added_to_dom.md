---
title: "Active Directory integration: computer added to domain but login doesn't work"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Saghaulor on 2009-05-11
Per this [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

and per this
[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/")

I was able to join my desktop to a Windows domain with Active Directory.

But I cannot log in.

When I run 
```
wbinfo -u
```
I receive a list of all users in Active Directory, so I know it's working, sort of.

But I can't figure out how to log into my Ubuntu desktop using my user login supplied by Active Directory.

Any ideas?

---

