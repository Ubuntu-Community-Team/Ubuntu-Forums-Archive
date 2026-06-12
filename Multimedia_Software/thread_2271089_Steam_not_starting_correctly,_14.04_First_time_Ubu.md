---
title: "Steam not starting correctly, 14.04? First time Ubuntu user, help!!"
date: 2015-03-27
forum: Multimedia Software
---

### Post by ajpocan on 2015-03-27
Hello everyone I am completely new to Ubuntu and I tried downloading steam from USC and every time I try to open and load the program it gives me the same problem. First, when I click to open steam, it gives me terminal (which I think is normal) to enter my password. I did notice though, that when this first screen opens it says that steam needs to download "these additional packages: libgli-mesa-dri:i386, libgli-mesa-glx:i386" So at this point I put in my password (thinking it will just install the packages when updating steam if necessary.) When I put in my password it then says this in terminal:


"reloading package lists... done
building dependency tree
reading state information... done
some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of incoming. 
The following information may help to resolve the situation:


The following packages have unmet dependencies:
libgli-mesa-glx:i386 : depends: libgli-mesa:i386 (= 10.1.3-0ubuntu0.4)
unity-control-center : depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver: :Resolve generated breaksm this may be caused by held packages.
Press return to continue:"


So I press enter and I recieve this message:
"Error
You are missing the following 32-bit.libraries, and Steam may not run:
libGL.so.1"


Then Steam tries to quickly update and I recieve this:
"Steam - Fatal Error
Fatal Error: Failed to load steamui.so"


What do I do from here? I have tried uninstalling and re-installing and that doesn't help. I have tried some commands in terminal but they all have come back and said that it cannot locate the packages I requested. 


Thanks a million in advance!

---

### Post by mc4man on 2015-03-27
Run this in a terminal, post the results (ctrl+alt+t to open a terminal) copy & paste the command & results, you made a typo in your post, it's libgl1..., not libgli...
```
apt-cache policy libgl1-mesa-glx-lts-utopic
```

---

### Post by ajpocan on 2015-03-28
Woo hoo, it worked! As a new member of the Ubuntu community, I thank you a million times over :D

---

### Post by Rob Sayer on 2015-03-28
Good, try marking your thread [SOLVED] so others can find your solution better.

---

### Post by sayvanfire on 2015-03-28
So, how do I fix it? This is what comes up:

libgl1-mesa-glx-lts-utopic:
  Installed: 10.3.2-0ubuntu1~trusty2
  Candidate: 10.3.2-0ubuntu1~trusty2
  Version table:
 *** 10.3.2-0ubuntu1~trusty2 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by mc4man on 2015-03-28
> **sayvanfire said:**
> So, how do I fix it? This is what comes up:

libgl1-mesa-glx-lts-utopic:
  Installed: 10.3.2-0ubuntu1~trusty2
  Candidate: 10.3.2-0ubuntu1~trusty2
  Version table:
 *** 10.3.2-0ubuntu1~trusty2 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
fix with
```
sudo apt-get install libgl1-mesa-glx-lts-utopic:i386
```

---

