---
title: "Problem: Samba passwords automatically changed to Unix password"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by Psylarium on 2010-01-31
I had a problem with Ubuntu 9.10, when using a samba config file that was working fine with Ubuntu 8.04, my samba password was getting replaced automatically after a few hours by my Unix password.

I had this option set:
[FONT=Courier New][FONT=&quot]unix password sync = no[/FONT][/FONT]
But that didn't help, the passwords were still getting replaced.

So to cut short a long story I finally figured it out, I had to uninstall:
[FONT=Courier New]pam_smbpass[/FONT]
This somehow was installed automatically by Ubuntu. And that was the module creating the issue by syncing Samba and Unix passwords by replacing the Samba one.

A more complete explanation can be found on my blog:
[http://psylarium.blogspot.com/2010/01/my-samba-server-was-losingchanging.html](http://psylarium.blogspot.com/2010/01/my-samba-server-was-losingchanging.html)

---

