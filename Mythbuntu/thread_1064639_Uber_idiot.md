---
title: "Uber idiot"
date: 2009-02-09
forum: Mythbuntu
---

### Post by el_heffe on 2009-02-09
OK, I am impressed this worked, but it somehow does.  I currently have a AMD64 mythbuntu installed on top of a Core2Duo Allendale core.  Is there a way to change this without having to reinstall everything, as it is causing some interesting dependency freakouts.  Oddly, everything is stable and working, but I can't get mencoder installed to transcode...  Any help is appreciated!!

---

### Post by ian dobson on 2009-02-09
Hi,

Core2Duo's support 64bit, and as AMD created the first 64bit CPU (which Intel copied almost too the letter) the linux programmers called it AMD64.

How are you trying to install memcoder? Please provide abit more information, it's easier to help:P

Regards
Ian Dobson

---

### Post by el_heffe on 2009-02-09
> **ian dobson said:**
> Hi,

Core2Duo's support 64bit, and as AMD created the first 64bit CPU (which Intel copied almost too the letter) the linux programmers called it AMD64.

How are you trying to install memcoder? Please provide abit more information, it's easier to help:P

Regards
Ian Dobson

I am trying to install it via apt.

```
 
mythbuntu:~$sudo apt-get install mencoder
[sudo] password for <*******>: 
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
  mencoder: Depends: libtwolame0 but it is not installable
E: Broken packages
mythbuntu:~$ sudo apt-get install libtwolame0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libtwolame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtwolame0 has no installation candidate


```

Any ideas are much appreciated!

---

### Post by el_heffe on 2009-02-15
It still isn't working, anyone have any ideas?

---

