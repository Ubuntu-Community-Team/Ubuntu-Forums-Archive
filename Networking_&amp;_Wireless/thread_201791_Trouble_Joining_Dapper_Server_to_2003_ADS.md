---
title: "Trouble Joining Dapper Server to 2003 ADS"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by krw on 2006-06-22
I've followed the [HowTo here](http://www.ubuntuforums.org/archive/index.php/t-91510.html) and was able to successfully run 

```
net ads join -U domainadminuser@DOMAIN.INTERNAL
```

However, after  I bounced the Ubuntu box I'm now not able to log into it with any AD or local username/password combos. I can only get into the Ubuntu box using the system recovery boot option. When I log in that way I can successfully run both

```
kinit domain_admin_account@DOMAIN.INTERNAL
```
and
```
net ads join -U domainadminuser@DOMAIN.INTERNAL
```
and I get the message after running "net ads join" that the account already exists and it is being updated.

Thanks in advance for any help you can give me.

---

