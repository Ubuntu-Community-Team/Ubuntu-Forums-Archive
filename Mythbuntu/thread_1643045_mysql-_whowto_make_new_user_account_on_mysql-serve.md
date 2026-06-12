---
title: "mysql- whowto make new user account on mysql-server On my mythbuntu box."
date: 2010-12-11
forum: Mythbuntu
---

### Post by gunnartr on 2010-12-11
When I try to make new user I get the following error.: ERROR 1227 (42000): Access denied; you need the CREATE USER privilege for this operation
I am logged in as mythtv user with pw according to that user. I have tried to log in as root, as user with root privilege without any luck. I wanted to make use of the mysql-server and make my own database to experiment with, but I lack the skills.
Can anyone help me find out howto login with necessary privilege to add a new user.

---

### Post by thespirit3 on 2011-04-05
I know this is an old post - but I've just hit exactly the same issue.  Mythbuntu 10.10 doesn't have the root mysql user password set as empty.   The mythtv user doesn't have create user privileges.

Help?

Update: Found this elsewhere - the root mysql password is by default the same as your users (unix account) password...

---

