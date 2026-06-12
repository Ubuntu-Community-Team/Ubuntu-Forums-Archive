---
title: "mythbuntu-control-center not working"
date: 2008-10-18
forum: Mythbuntu
---

### Post by TheConsultant on 2008-10-18
Hi.

My MCC will not work even if I start it out of the mythfrontend nor manual. Screenshot is attached.

Have anybody suggestions?

Best regards

Martin

---

### Post by superm1 on 2008-10-18
> **TheConsultant said:**
> Hi.

My MCC will not work even if I start it out of the mythfrontend nor manual. Screenshot is attached.

Have anybody suggestions?

Best regards

Martin
That second error is caused from running it through putty without DISPLAY set.

The first error appears to be something wrong with parsing /etc/passwd.  Can you post your /etc/passwd file to a bug filed against MCC with this same stuff discussed?

Please file the bug at:

[http://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre](http://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre)

---

