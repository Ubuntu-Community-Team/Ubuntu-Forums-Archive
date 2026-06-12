---
title: "Active Directory and PAM set up"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by zorro2b on 2010-11-16
I have set my Ubuntu 10.04 box with our Windows domain. I can see from "net ads info" that I am on the domain. I can also get the password and group info with getent.

So far so good. But I have tried to configure pam basically by following this guide:
[http://www.ccs.neu.edu/home/battista/documentation/winbind/pam.html](http://www.ccs.neu.edu/home/battista/documentation/winbind/pam.html)

Yet when I try to su or login as an AD user I just get and immediate "Unknown id: <userid>"

I have had a look at /var/log/auth.log and there are no errors there.

Can anyone provide some tips on debugging the pam configuration?

thanks,
Andrew

---

### Post by puppywhacker on 2010-11-16
There is a PAM debug module
[http://manpages.ubuntu.com/manpages/hardy/man8/pam_debug.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_debug.8.html)

But your link seems pretty weak compared to the Ubuntu help on AD/Winbind
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

