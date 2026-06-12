---
title: "The package is of bad quality - Can't install Chrome"
date: 2011-02-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2011-02-28
I have been using google-chrome*deb to install for a long time. Even on alpha1 it installed.
but I got a unforeseen message this time from ubuntuone - **The package is of bad quality**, with the following error. 
```
Lintian check results for /home/vmc/chrome-9.0.597.98-r74359_amd64.deb:
Can't call method "data" on an undefined value at /usr/share/lintian/checks/deb-format line 63. 
internal error: cannot run deb_format check on package google-chrome-stable 
warning: skipping check of binary package google-chrome-stable 
md5sum: ./etc/cron.daily/google-chrome: No such file or directory
```

Anyone else see this before?

---

### Post by ikt on 2011-03-01
[https://bugs.launchpad.net/bugs/712377](https://bugs.launchpad.net/bugs/712377)

---

### Post by VMC on 2011-03-01
> **ikt said:**
> [https://bugs.launchpad.net/bugs/712377](https://bugs.launchpad.net/bugs/712377)

Thank you. I though it was just something wrong with my new install. First time I was able to use natty in well of two weeks.

Reading that report, I was about to install gdebi and try that one, but got sidetrack. I have me-too that bug report. thanks again for looking.

---

### Post by rworloma on 2011-04-18
You can read this post at [Liberian Geek]("http://www.liberiangeek.net/2011/04/install-gdebi-package-installer-and-fix-the-package-is-of-bad-quality-error-in-ubuntu-11-04-natty-narwhal/") to install packages that give you that error.

---

