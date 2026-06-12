---
title: "In case you can't open software sources"
date: 2010-10-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2010-10-13
```
sudo vim /usr/share/python-apt/templates/Ubuntu.info

```
and add the following before the line "Suite: maverick"
> Suite: natty
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 11.04 'Natty Narwhal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: natty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.04
MatchURI: cdrom:\[Ubuntu.*11.04
Description: Cdrom with Ubuntu 11.04 'Natty Narwhal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: natty
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: natty
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.


Suite: natty-security
ParentSuite: natty
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb
Description: Recommended updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb
Description: Pre-released updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb
Description: Unsupported updates


---

### Post by Framli on 2010-10-13
Thanks for the tip!

---

### Post by Slug71 on 2010-10-13
Was hoping that would be fixed for Natty.

---

### Post by Vanishing on 2010-10-13
> **Slug71 said:**
> Was hoping that would be fixed for Natty.

apparently not.:P

---

### Post by andymorton on 2010-10-13
It's saying ''vim: command not found'' 

:(

---

### Post by Vanishing on 2010-10-13
> **andymorton said:**
> It's saying ''vim: command not found'' 

:(

:(..maybe you ought to substitute vim with gedit...
try it..:)

---

### Post by cariboo on 2010-10-13
Or even nano. :)

---

### Post by andymorton on 2010-10-13
> **Vanishing said:**
> :(..maybe you ought to substitute vim with gedit...
try it..:)

Thanks!

---

### Post by sisco311 on 2010-10-13
@Vanishing

Thanks!

> **cariboo907 said:**
> Or even nano. :)

+1 for nano. Not because I like it, but it's installed by default.

---

### Post by ranch hand on 2010-10-13
Or you could go to Synaptic and try to get in from there.  I haven't had trouble with either so it may well be that neither will work.

---

### Post by Vanishing on 2010-10-13
> **ranch hand said:**
> Or you could go to Synaptic and try to get in from there.  I haven't had trouble with either so it may well be that neither will work.

So they fixed it? :popcorn:

---

### Post by xebian on 2010-10-13
Or simply %s/maverick/natty/g in vim.

---

### Post by Vanishing on 2010-10-13
> **xebian said:**
> Or simply %s/maverick/natty/g in vim.

unless you want to wipe the maverick branch out in that file..:P

---

### Post by Reiger on 2010-10-14
“if” instead of “unless”. Lest people do inadvertently search & replace all mavericks with natties.

---

### Post by zika on 2010-10-14
> **Vanishing said:**
> ```
sudo vim /usr/share/python-apt/templates/Ubuntu.info

```
and add the following before the line "Suite: maverick"Is it my age or my endogenous level of intelligence, but I forget on this little change every time new testing starts! Thank You...
The only excuse is a withdrawal anxiety I feel several weeks before a release is released... :)

---

### Post by MacUntu on 2010-10-19
11.4 -> 11.04 ;)

---

### Post by Harry33 on 2010-10-20
This is fixed now with this update:
“python-apt” 0.7.98.1ubuntu1 source package in The Natty Narwhal
It is at the moment "NEW".
But of course you may download the files from launchpad and use dpkg.

---

### Post by Vanishing on 2010-10-20
> **MacUntu said:**
> 11.4 -> 11.04 ;)

right...:popcorn:
please pardon my poor math skills.:(

---

### Post by MacUntu on 2010-10-20
> **Vanishing said:**
> 
please pardon my poor math skills.:(

If it's any comfort to you, you are not alone: [http://www.google.com/search?q=%22Ubuntu+10.4%22](http://www.google.com/search?q=%22Ubuntu+10.4%22) :P

---

### Post by JOHNNYG713 on 2010-10-20
Thanks for this thread ! :)

---

### Post by Harry33 on 2010-10-21
> **Harry33 said:**
> This is fixed now with this update:
“python-apt” 0.7.98.1ubuntu1 source package in The Natty Narwhal
It is at the moment "NEW".
But of course you may download the files from launchpad and use dpkg.

And if you do choose this manual installation method,
note that package python-apt now depends on python-apt-common too.
Here:
[https://launchpad.net/ubuntu/natty/+source/python-apt/0.7.98.1ubuntu1](https://launchpad.net/ubuntu/natty/+source/python-apt/0.7.98.1ubuntu1)

---

