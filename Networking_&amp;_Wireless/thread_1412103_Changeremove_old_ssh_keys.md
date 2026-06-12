---
title: "Change/remove old ssh keys"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by JohnYYC on 2010-02-20
So I have sshopen-server installed on a few machines on my home network. I just rebuilt one of the machines and gave it the same hostname and the same ip address that it had before I rebuilt it. But when I go to connect to the machine now I get this error.

```

john@SILO:~$ ssh mom@mom
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
*removed key number*.
Please contact your system administrator.
Add correct host key in /home/john/.ssh/known_hosts to get rid of this message.
Offending key in /home/john/.ssh/known_hosts:9
RSA host key for mom has changed and you have requested strict checking.
Host key verification failed.
john@SILO:~$ 

```

Can I safely delete line 9 in the /home/john/.ssh/known_hosts and then try and reconnect?

---

### Post by chili555 on 2010-02-20
Yes, you may, assuming this is a trusted home network.

---

### Post by JohnYYC on 2010-02-20
Yea this is just on my home network. SSH is not accessible to the internet just the intranet. So I deleted line 9 from my /home/john/.ssh/known_hosts file, reconnected and everything works now.

Thanks for confirming that for me.

---

