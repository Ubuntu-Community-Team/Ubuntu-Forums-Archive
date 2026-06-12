---
title: "Mac LDAP Authentication Problems"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by sliggy on 2008-12-30
Hey everyone,

I just followed [this](https://help.ubuntu.com/community/OSXLDAPClientAuthentication) guide on how to setup Ubuntu to authenticate with an Mac OS X 10.4 server. I followed the guide 100% and was left with the ability to see users by running 
```
getent passwd
and
getent passwd (user)
```
Which would come up with all the right information about the user. My problem is that I want those users to be able to login through the login prompt, which isn't working. When I login as my local user though, I get the usual username and password prompt, but then I get an LDAP password prompt, where I can type in anything and still login successfully. 

Any ideas on how to solve this? Thanks in advance!

---

### Post by sliggy on 2009-01-05
Sorry for the bump, but does anyone have a solution to this?

---

### Post by iank2112 on 2009-01-16
Try this in common-account:

account sufficient      pam_succeed_if.so uid < 500 quiet
account [user_unknown=ignore success=ok default=bad] pam_ldap.so use_first_pass
account required        pam_unix.so use_first_pass

common-auth:

auth    sufficient      pam_ldap.so use_first_pass 
auth    required        pam_unix.so nullok_secure use_first_pass
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel

and common-session:

session sufficient      pam_ldap.so use_first_pass
session required        pam_unix.so use_first_pass
session optional        pam_foreground.so
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel

I am using Open Directory on 10.5, and have Kerberos running
as well, and it works for me just fine.

Ian

---

### Post by sliggy on 2009-08-11
> **iank2112 said:**
> Try this in common-account:

account sufficient      pam_succeed_if.so uid < 500 quiet
account [user_unknown=ignore success=ok default=bad] pam_ldap.so use_first_pass
account required        pam_unix.so use_first_pass

common-auth:

auth    sufficient      pam_ldap.so use_first_pass 
auth    required        pam_unix.so nullok_secure use_first_pass
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel

and common-session:

session sufficient      pam_ldap.so use_first_pass
session required        pam_unix.so use_first_pass
session optional        pam_foreground.so
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel

I am using Open Directory on 10.5, and have Kerberos running
as well, and it works for me just fine.

Ian

Sorry for the bump, but I tried this with no luck. Does anyone else have any ideas for a solution?

---

### Post by sliggy on 2009-08-13
Bump again, I really need help for this...

---

### Post by sliggy on 2009-08-25
Can someone please help me with this?

---

