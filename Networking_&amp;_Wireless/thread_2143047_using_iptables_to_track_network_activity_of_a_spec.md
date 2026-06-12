---
title: "using iptables to track network activity of a specific program"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2013-05-07
With iptables it is possible to use *--uid-owner* to filter based on a particular user.  Is there something that can filter on a specific application?  Or would the only way to monitor an individual app be to launch it in a unique group and use *--gid-owner* to filter?

---

### Post by Doug S on 2013-05-07
Evidently, there used to be a way via "--cmd-owner name", but it got removed because it broke. I think you have to do as you suggested.

References:
[http://ubuntuforums.org/showthread.php?t=1739672](http://ubuntuforums.org/showthread.php?t=1739672)
[http://www.linuxquestions.org/questions/linux-security-4/iptables-output-rules-drop-by-process-pid-65893/](http://www.linuxquestions.org/questions/linux-security-4/iptables-output-rules-drop-by-process-pid-65893/)
[https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/800781](https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/800781)
There seems to be plenty of confusing stuff using search engine terms: iptables "--cmd-owner" removed

---

### Post by Lars Noodén on 2013-05-08
Thanks.  Also, thinking about it further, if the program is launched under a unique group any child processes it might spawn overtly or covertly will (most likely) also fall under that group.

---

### Post by Lars Noodén on 2013-05-08
Now, how, with this new layout, is a thread marked "solved" ?

---

### Post by Elfy on 2013-05-08
For the time being - [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)

---

### Post by Lars Noodén on 2013-05-08
Thanks.  I saw instructions like those before but only now figured out that they only work when it is the first post in the thread that gets edited.  All set now.

---

