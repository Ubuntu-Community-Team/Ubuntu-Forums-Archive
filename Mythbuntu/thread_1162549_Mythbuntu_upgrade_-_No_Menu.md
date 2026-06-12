---
title: "Mythbuntu upgrade - No Menu"
date: 2009-05-17
forum: Mythbuntu
---

### Post by korgman on 2009-05-17
I upgraded Mythbuntu tonight to 9.04 and I have no main menu when the PC boots up into MythTv. If I hit 'ENTER', it will jump right into watching live TV. The guide works, the remote works, just no main menu.  And I get this when I do an update

```
The following extra packages will be installed:
  mythbuntu-log-grabber
The following packages will be upgraded:
  mythbuntu-log-grabber
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/11.4kB of archives.
After this operation, 16.4kB disk space will be freed.
Do you want to continue [Y/n]? Y   
(Reading database ... 158215 files and directories currently installed.)
Preparing to replace mythbuntu-log-grabber 0.1-0ubuntu2 (using .../mythbuntu-log-grabber_0.3-0ubuntu1_amd64.deb) ...
Adding `diversion of /usr/share/mythtv/util_menu.xml to /usr/share/mythtv/util_menu.xml.diverted by mythbuntu-log-grabber'
dpkg-divert: rename involves overwriting `/usr/share/mythtv/util_menu.xml.diverted' with
  different file `/usr/share/mythtv/util_menu.xml', not allowed
dpkg: error processing /var/cache/apt/archives/mythbuntu-log-grabber_0.3-0ubuntu1_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/mythbuntu-log-grabber_0.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Any ideas?

---

### Post by korgman on 2009-05-17
New info, upon boot, the backend log is in an infinite loop reporting every second...

QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.

If i hit enter and begin watching live tv, the msg stops.
mattbrown is online now Report Post   	Edit/Delete Message

---

### Post by pjw1965 on 2009-05-18
Did you read the [http://www.mythbuntu.org/9.04/Release_notes](http://www.mythbuntu.org/9.04/Release_notes) ?

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898/comments/59](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898/comments/59) helped me, if you also use a radeon video card.

---

