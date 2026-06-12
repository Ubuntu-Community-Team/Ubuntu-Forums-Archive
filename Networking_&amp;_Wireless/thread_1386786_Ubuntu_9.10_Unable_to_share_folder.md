---
title: "Ubuntu 9.10 Unable to share folder"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by gseward on 2010-01-21
I am unable to share a folder on my Ubuntu 9.10 desktop machine.  Networking is working, I can see and be seen by windows machines and also my Ubuntu 9.10 laptop.  The laptop is able to share folders with no problem.  The error message I get when I try to set sharing on a folder is
 "'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error."

I know there has been a thread relating to this in the past, but the solution there did not work for me, and I have been beating my head against the wall for a couple of weeks on this problem, and have spent a bit of time with smb.conf.  I would hate to have to do a new install to fix this, after all this is not MS windows!
Can anyone point me in the right direction?

---

### Post by Iowan on 2010-01-21
I was just searching for 'cannot convert name "Everyone" to a SID' and found [this]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/334949") bug report. Setting security=share seems to be another way to fix it - certainly not optimum...
[Another]("http://ubuntuforums.org/showthread.php?t=958457") solution.

---

