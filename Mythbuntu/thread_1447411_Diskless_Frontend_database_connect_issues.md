---
title: "Diskless Frontend database connect issues"
date: 2010-04-05
forum: Mythbuntu
---

### Post by SilkBC on 2010-04-05
Hello.

I am running MythBuntu 9.10.  I have followed the instructions for setting up the diskless server manually at [https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless"), and I can get a diskless front end up.

I start MythTV Frontend on it for the first time and it of course runs me through the initial setup wizard.  I enter the database information, but then I get a screen that says:

```
Cannot find (ping) database host on the network
```

I have tried using the hostname and the IP and they both give the same error.  From a terminal on the diskless front end, I am able to connect manually using

```
mysql -h 10.215.1.2 -u mythtv -p mythconverg
```

It then of course asks me for the password, which I enter and it connects me no problem.  I can list the tables, the data, etc.  I also opened the control center on the diskless front end and made sure the database information in there was correct; the "test connectivity" test was successful.

Not sure if I have missed something?

Thanks, in advance, for your insight on this.

-SilkBC

---

