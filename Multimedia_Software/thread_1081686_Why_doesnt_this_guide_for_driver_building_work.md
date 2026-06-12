---
title: "Why doesnt this guide for driver building work?"
date: 2009-02-26
forum: Multimedia Software
---

### Post by Daremo_06 on 2009-02-26
I'm still looking for a solution to dual display with ATI 9200 and Intrepid and in my searching today, I found this on the ubuntu documentation page.

[https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI)

1st of all, the editing of the radeon_bios.c doesnt appear to be needed now as there is no blocked out section of code as described by the guide.

next when attempting to build the driver I get the following...

> rob@rob2:~/Desktop/build$ dpkg-buildpackage -rfakeroot -uc -b
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1

So whats going wrong here?  Also, is this guide useless for Intrepid?  If so, shouldn't the documentation be updated?

Thanks,
Rob

---

### Post by hansdown on 2009-02-26
Hi Daremo_06.

That guide is seriously outdated for 8.10.

I don't know if any of these will help.

[http://www.google.ca/search?q=dual+display+with+ATI+9200+and+Intrepid+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=dual+display+with+ATI+9200+and+Intrepid+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Daremo_06 on 2009-02-26
which brings me to the 2nd question, shouldnt that document be updated???  I had a feeling it wasnt going to work when it was talking about older releases, but i was hoping that the documentation was kept up to date.

---

### Post by hansdown on 2009-02-26
You're absolutely right, but there is constantly new things added, and nobody knows these things are old until someone lets them know.

---

