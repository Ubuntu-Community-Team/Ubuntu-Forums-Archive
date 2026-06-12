---
title: "Removing a 'broken' package"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by Pixtu on 2009-03-26
I wanted to try and monitor network usage and therefore, following advice in another thread, I tried to install bandwidthd. However, it fails to install and when I try and remove it I get the message that the package should be installed first.

I also have some additional packages that it is suggested can be removed, but these appear to fail as well, I believe because of the bandwidthd problem.

I have tried apt-get install, apt-get remove and apt-get purge.

I have enclosed the apt-get output in case it helps.

Any other ideas please?

```
stuart@Sony-LT:~$ sudo apt-get install bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/71.8kB of archives.
After this operation, 57.3kB of additional disk space will be used.
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure with exit status 1.
(Reading database ... 202808 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20071208-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB style header
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
stuart@Sony-LT:~$ sudo apt-get remove bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bandwidthd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)
stuart@Sony-LT:~$
```

---

### Post by x33a on 2009-03-26
open synaptic, click on broken, see if the package is listed there. if it is, then click edit -> fix broken packages.

---

### Post by Pixtu on 2009-03-28
Hi x33a

Thanks for your reply.

The package is not listed as 'broken'. I tried marking it for complete removal but when I click apply changes I get the same problem - it fails the task with the suggestion that the 'package is in a bad state'.

I seem to be stuck in an impossible loop. It needs to be installed/re-installed in order to remove it, but it can't be installed because the package seems incomplete.

Is there some way I can force a broken state?

---

### Post by Claus7 on 2009-03-28
Hello,

does the second post tell you anything? I would advice you to read also the first one in case you find similar issues with your case.
[http://ubuntuforums.org/showthread.php?t=1084491](http://ubuntuforums.org/showthread.php?t=1084491)
It took me months to solve my broken packages, yet afterwards everything was back to normal. It depends on the broken package. Other than that you might have to go manually to where the package is and remove the files yourself, yet you have to know there exactly what you are doing. Do it with the "easy" way first.

Regards!

---

### Post by Pixtu on 2009-03-28
Found at least part of the answer on another thread - Credit to user 'plucky' for the answer.
[http://ubuntuforums.org/showpost.php?p=6732820&postcount=14](http://ubuntuforums.org/showpost.php?p=6732820&postcount=14)

This post details where synaptic holds its package status information. If you change the package name in the post to the package you're having problems with, it should enable you to at least use synaptic again.:)

I suspect that there are still some files left lying around which I will try and get rid of, but at least it is no longer a 'show stopper'.

---

