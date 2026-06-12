---
title: "ldap authentication app"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by vince stein on 2010-12-24
What I would like to do is create an application that takes a username and password, queries an ldap, and returns a boolean denoting whether that was a valid username/password combination.

I messed around with the command "ldapsearch", and I can search anonymously, but if I give my password with -w, I get "invalid credentials."  But my password *is* correct, so it sounds to me like it wants the ldap's admin's password, which is not how I want my application to work.

This should be simple enough, but I just don't get it.  Thanks.

---

