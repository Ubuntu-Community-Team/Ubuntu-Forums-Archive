---
title: "Blueman 1.10 Python Header problem"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by iKevin09 on 2009-05-29
Okay, so I'm in kevintran@kevintran-desktop:~/blueman-1.10$ right now, right? I type in "./configure" and it starts spitting out random junk, now this is at the end of the junk. Apparently there's an error with Python and its headers? Here's part of the Terminal text:

checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... /usr/lib/python2.6/dist-packages
checking for python extension module directory... /usr/lib/python2.6/dist-packages
checking for headers required to compile python extensions... not found
configure: error: Could not find Python headers
kevintran@kevintran-desktop:~/blueman-1.10$ 

Please help me!

I don't have Internet on Ubuntu, I do, however have Internet on Windows XP as a dualboot on the same computer.
I'm installing Blueman so I can tether using Ubuntu. I want to have a reliable and stable OS, not Microsoft's insanely unstable OS's.

---

### Post by iKevin09 on 2009-05-29
Bump?

---

### Post by iKevin09 on 2009-05-29
Anybody? At all?

---

### Post by redxine on 2009-07-16
Don't know if it's too late or not..... but to get blueman working:
```
sudo apt-get install python-dev
```

But that would fail as you need an internet connection. You could just use the deb from launchpad: [https://edge.launchpad.net/~blueman/+archive/ppa](https://edge.launchpad.net/~blueman/+archive/ppa)

---

