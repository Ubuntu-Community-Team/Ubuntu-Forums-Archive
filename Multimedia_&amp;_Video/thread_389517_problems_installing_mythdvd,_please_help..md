---
title: "problems installing mythdvd, please help."
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by electronikjunkie on 2007-03-20
i installed mythtv from svn and now i'm trying to install mythdvd, but i get broken dependencies errors. here is the output:
```
joesmoe@mycomputerk:~$ sudo apt-get install mythdvd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythdvd: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is to be installed
           Depends: libiec61883-0 (>= 1.1.0) but 1.0.0-0.2ubuntu1 is to be installed
           Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3 is to be installed
E: Broken packages
```

i don't know how to fix this, could someone help me out? thanks in advance for your help.

---

### Post by fenian on 2007-03-20
The versions of those programs are newer than the versions of those in the edgy repositories.I don't knw where you would find those versions or if they would work if you did.Is there a reason you are installing the svn version rather than the one in the repos?I have installed several versions from the repos and they work great.There is a good wiki for mythtv ubuntu [here]("https://help.ubuntu.com/community/MythTV_Edgy?highlight=%28mythtv%29").

---

### Post by electronikjunkie on 2007-03-20
i've only had luck playing smooth hdtv content with mythtv svn, i tiried everything. it took me 3 months to get it working correctly. do you think i can just go get the dependencies as svn and it will satisfy the dependencies listed?

---

### Post by electronikjunkie on 2007-03-21
if i add these repositories will i be able to install the dependent packages listed above?
```

deb http://archive.ubuntu.com/ubuntu/  feisty           main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/  feisty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/  feisty-updates   main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ feisty-security  main restricted universe multiverse
```

by adding these repos will it mess up my system or get in the way of the edgy repos listed in "/etc/apt/sources.list".

---

