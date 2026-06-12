---
title: "Error installing pepperflashplugin-nonfree on Ubuntu 14.10"
date: 2014-11-06
forum: Multimedia Software
---

### Post by arashiko28 on 2014-11-06
Hello, I've been trying to install the flash player for chrome but keep coming across several problems.

For chromium, it's supposed to be pepperflashplugin-nonfree so flash media could be played, how ever, this is what I get when I try it:

```
 sudo apt-get install pepperflashplugin-nonfree
[sudo] password for arashiko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pepperflashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded. 
```

```
 sudo update-pepperflashplugin-nonfree --install
--2014-11-06 10:53:42--  http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_38.0.2125.111-1_i386.deb
Resolving dl.google.com (dl.google.com)... 74.125.229.137, 74.125.229.132, 74.125.229.128, ...
Connecting to dl.google.com (dl.google.com)|74.125.229.137|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 175 [text/html]
Saving to: ‘/tmp/pepperflashplugin-nonfree.A1kXPrdSNY/google-chrome-stable_38.0.2125.111-1_i386.deb’

     0K                                                       100% 3.68M=0s

2014-11-06 10:53:43 (3.68 MB/s) - ‘/tmp/pepperflashplugin-nonfree.A1kXPrdSNY/google-chrome-stable_38.0.2125.111-1_i386.deb’ saved [175/175]

ERROR: rejecting google-chrome-stable_38.0.2125.111-1_i386.deb : wrong size
More information might be available at:
  http://wiki.debian.org/PepperFlashPlayer
```

Any Ideas on how to fix it? BTW the wiki page contains no information about it.

---

### Post by arashiko28 on 2014-11-11
Soo... there's no way to run flash on Ubuntu from now on???

---

### Post by mc4man on 2014-11-11
I don't have 14.10 but do you have anything in /usr/lib/pepperflashplugin-nonfree folder

---

