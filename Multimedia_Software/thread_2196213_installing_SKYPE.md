---
title: "installing SKYPE"
date: 2013-12-28
forum: Multimedia Software
---

### Post by christon74 on 2013-12-28
Good evening every and all Ubunters :D
I have just downloaded SKYPE for Linux but I cannot find the right application to install it.
The software center will not do it (for God knows what damn reason)_ Archive mounter is not of much help either.  Could it be I have not downloaded the right version of SKype?  [Skype-ubuntu-precise_4.2.0.11-1_i396.deb]

Any piece of advice highly welcome. 
Thanks in advance for all help and trouble.
Chris.;-)

---

### Post by ian-weisser on 2013-12-29
The recommended way of installing Skype is to use the version in the Ubuntu Partner repositories.
Open a terminal and try the following commands.
If you get an error, stop and paste the complete terminal session here.
```
sudo apt-add-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype
```

---

### Post by christon74 on 2014-01-23
Thank you Ian. :)- I have finally installed SKYPE; This thread is solved.

---

### Post by Bob_Lade on 2014-02-25
Ian, that did not work for me. I get the following errors:
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Any ideas? I'm a brand new Linux/Ubuntu user (but experienced Windoz user.) Any help would be appreciated... Thanks!

---

### Post by ian-weisser on 2014-02-25
Bob_Lade,
Your error is unrelated to Skype. Searching this forum for that particular error message will quickly lead you to the solution.

---

### Post by Simon_WM on 2014-02-25
Why don't you download the DEB file direct from Skype, or install from the market place?

---

### Post by ian-weisser on 2014-02-25
That won't solve Bob_Lade's problem, which is a corrupted file only tangentially related to Skype, already on his system, very simple to fix, and irrelevant to this thread.
Also, the original poster in this thread DID download from Skype, and was asking how to install the file they downloaded.
If you have problems installing Skype that are different from that original poster's issue, please open a NEW thread.

---

