---
title: "Mount /home from remote location"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by mejborn on 2009-08-08
Hi all,

I've searched the forum withrout any luck regarding my question.

Does any of you have a guide of something that I can use to get started with mounting my /home from a server on my LAN?

I have several Ubuntu machines on my network and I would like to have the same /home mounted on all machines.

Best regards

Mathias

---

### Post by scorp123 on 2009-08-08
> **mejborn said:**
>  Does any of you have a guide of something that I can use to get started with mounting my /home from a server on my LAN? You mean NFS?

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by mejborn on 2009-08-08
Yeah I ment NFS, but I wasn't sure how to configure the client (/etc/fstab) and so.

I will look into the posted howto, thanks!

Best regards

Mathias

---

### Post by mejborn on 2009-08-08
Thanks I got it to work, but now it seems like I can't do any root tasks, iam getting a:

Unable to copy the user's Xauthorization file

If I try to do an update or run any program that requires root rights?

Best regards.

Mathias

---

### Post by scorp123 on 2009-08-08
> **mejborn said:**
> Thanks I got it to work, but now it seems like I can't do any root tasks This is normal. It's called "root_squash". Please read here:

[http://ubuntuforums.org/showpost.php?p=4184680&postcount=122](http://ubuntuforums.org/showpost.php?p=4184680&postcount=122)

Yes, "root_squash" can be turned off ... but then anyone claiming to be "root" gets full unlimited powers over _ANYTHING_ that is on that share. So if you have friends who have access to your network (shared WiFi maybe?) and who might think that it is funny to quickly remove all your files just for the fun to see you screaming and crying then you better DON'T TOUCH THIS.

Also: you should limit who can connect to your NFS shares and who can't. That's still pretty far from perfect security, but better than nothing.

---

