---
title: "Samba / Winbind - Unable to Authenticate"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by JoelCant on 2009-12-25
Does anyone have any suggestions as the why I cannot authenticate from my Ubuntu box to my AD domain.

WBinfo -u / -g / -K works, DNS is OK, joined to the domain ok, user accounts are fine, but I cannot login as a domain user.

Dec 25 21:39:28 jcws-005 su[20665]: pam_winbind(su:auth): getting password (0x00000000)
Dec 25 21:39:30 jcws-005 su[20665]: pam_winbind(su:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_SYSTEM_ERR (4), NTSTATUS: NT_STATUS_PIPE_DISCONNECTED, Error message was: Named pipe dicconnected
Dec 25 21:39:30 jcws-005 su[20665]: pam_winbind(su:auth): internal module error (retval = PAM_SYSTEM_ERR(4), user = 'test.user')
Dec 25 21:39:30 jcws-005 su[20665]: pam_unix(su:auth): authentication failure; logname=joel uid=1000 euid=0 tty=/dev/pts/0 ruser=joel rhost=  user=test.user
Dec 25 21:39:32 jcws-005 su[20665]: pam_authenticate: Authentication failure
Dec 25 21:39:32 jcws-005 su[20665]: FAILED su for test.user by joel
Dec 25 21:39:32 jcws-005 su[20665]: - /dev/pts/0 joel:test.user

The domain is W2K8 (Running server 2008 R2 dc's) Anyone any ideas as to why.

Joel

---

### Post by nmushov on 2011-02-25
Did you ever find a solution to this? I'm having the exact same problem.

---

