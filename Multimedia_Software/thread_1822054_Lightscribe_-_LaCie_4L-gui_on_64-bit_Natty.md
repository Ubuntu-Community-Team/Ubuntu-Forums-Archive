---
title: "Lightscribe - LaCie 4L-gui on 64-bit Natty"
date: 2011-08-10
forum: Multimedia Software
---

### Post by casperlingus on 2011-08-10
I just reinstalled my base system from 10.04 x64 to Natty 11.04 x64.  In 10.04, I installed all the Lightscribe software using the similar commands to what is referenced here:

_[http://ubuntuforums.org/showthread.php?t=809112](http://ubuntuforums.org/showthread.php?t=809112)_
```

sudo dpkg -i --force-architecture lightscribe-1.18.24.1-linux-2.6-intel.deb
sudo dpkg -i --force-architecture lightscribeApplications-1.18.15.1-linux-2.6-intel.deb
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
**sudo dpkg -i --force-architecture 4l_1.0-r6_i386.deb**

```

All these .deb packages are built for 32-bit architectures, but the --force-architecture flag has always worked.  So, both 8.04 and 10.04 the last line runs fine, but this time I get:  

```

casper@sekhmet:~/downloads$ sudo dpkg -i --force-architecture 4l_1.0-r6_i386.deb
[sudo] password for casper: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 203507 files and directories currently installed.)
Preparing to replace 4l:i386 1.0-r6 (using 4l_1.0-r6_i386.deb) ...
Unpacking replacement 4l:i386 ...
dpkg: dependency problems prevent configuration of 4l:i386:
 4l:i386 depends on libc6 (>= 2.6-1).
 4l:i386 depends on libfontconfig1 (>= 2.4.0).
 4l:i386 depends on libfreetype6 (>= 2.3.5).
 4l:i386 depends on libgcc1 (>= 1:4.2.1).
 4l:i386 depends on libstdc++6 (>= 4.2.1).
 4l:i386 depends on libx11-6.
 4l:i386 depends on libxcursor1 (>> 1.1.2).
 4l:i386 depends on libxext6.
 4l:i386 depends on libxi6.
 4l:i386 depends on libxinerama1.
 4l:i386 depends on libxrandr2 (>= 2:1.2.0).
 4l:i386 depends on libxrender1.
dpkg: error processing 4l:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 4l:i386

```

Now, I've verified that I have all these packages installed, and I've wandered through Synaptic and checked the versions of all the packages that explicitly indicate a version above -- those are all fine, too.   I found one other post [_here_]("http://www.linux-archive.org/ubuntu-user/552265-software-burn-lightscribe-disc.html") from a user with the exact same problem.  Then a couple posts later, he claims he solved it, but I see no solution :(

---

### Post by bcdudley on 2011-09-15
Did you ever come up with a solution for this. I am having the exact same problem with a different application.

 sudo dpkg -i --force-architecture 2XClient.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 151460 files and directories currently installed.)
Preparing to replace 2xclient:i386 10.0.1159 (using 2XClient.deb) ...
Unpacking replacement 2xclient:i386 ...
dpkg: dependency problems prevent configuration of 2xclient:i386:
 2xclient:i386 depends on libxcursor1 (>> 1.1.2).
 2xclient:i386 depends on zlib1g (>= 1:1.2.3.3.dfsg-1).
 2xclient:i386 depends on libfontconfig1 (>= 2.4.0).
 2xclient:i386 depends on libxrender1.
 2xclient:i386 depends on libc6 (>= 2.3.2).
 2xclient:i386 depends on libssl0.9.8.
 2xclient:i386 depends on libxfixes3 (>= 1:4.0.1).
 2xclient:i386 depends on libxrandr2 (>= 2:1.2.0).
 2xclient:i386 depends on libfreetype6 (>= 2.3.5).
 2xclient:i386 depends on libsm6.
 2xclient:i386 depends on libxtst6.
 2xclient:i386 depends on libice6 (>= 1:1.0.0).
 2xclient:i386 depends on libxext6.
 2xclient:i386 depends on libxi6.
 2xclient:i386 depends on libgcc1 (>= 1:4.1.1-21).
 2xclient:i386 depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35).
 2xclient:i386 depends on libxinerama1.
 2xclient:i386 depends on libxft2 (>> 2.1.1).
 2xclient:i386 depends on libx11-6.
dpkg: error processing 2xclient:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 2xclient:i386

---

### Post by joealanbrooks on 2011-09-15
I don't think the error messages are telling you it didn't install.  Try:

```
sudo 4L-gui
```

and see if it runs.

---

### Post by bcdudley on 2011-09-15
Not sure about the OP, but I can say for certain that mine did not install. I cannot run it from the cli and there are no menu items.

Thanks.

---

### Post by DFW on 2012-02-21
Try apt-get on the dependent 32 bit libs first:

sudo apt-get install ia32-libs

---

