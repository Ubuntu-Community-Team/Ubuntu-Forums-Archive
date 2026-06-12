---
title: "Bradford Dissolvable Agent sh"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by vinneh on 2010-02-20
My school network requires me to install Bradford Dissolvable Agent via a binary sh file.  I get this error:
```
Bradford_Dissolvable_Agent.sh: 2: Syntax error: EOF in backquote substitution
```This is on Ubuntu 9.10, x86 and amd64 on separate machines both return the same error.  Does anyone have any experience with this?  I have searched google and read through other threads, but they all cover a different issue related to libstdc++ (which I already have installed).  Any help would be greatly appreciated as I can't connect to the network until I run this stupid file.

---

### Post by vinneh on 2010-02-20
Never mind, my school sucks.  It was returning EOF because it actually was the end of file.  The file didn't download properly, but was still created with the name Bradford_Dissolvable_Agent.sh, so I kept trying to run it.  I'll have to get it in person.

---

### Post by lucasg123 on 2010-03-29
I have a little experience with that problem. If you are still seeking help let me know.

---

### Post by bunburya on 2010-05-30
> **lucasg123 said:**
> I have a little experience with that problem. If you are still seeking help let me know.
I have a similar problem on 10.04; basically whenever I try to run the program it returns some syntax errors (I can't copy-paste the output because it's on a different computer) and when I view the file with a text editor I get a load of gibberish, which I didn't think woul dhappen since it's a sh file. Do you think the file is corrupted? Have you had a similar problem?

---

