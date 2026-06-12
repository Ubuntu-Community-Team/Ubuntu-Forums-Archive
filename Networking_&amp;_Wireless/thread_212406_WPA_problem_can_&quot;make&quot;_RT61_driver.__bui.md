---
title: "WPA problem: can &quot;make&quot; RT61 driver.  build command not found."
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by adana on 2006-07-09
Trying to download/install RT61 driver.

Once it's downloaded, the instructions are:

$cp Makefile.6  ./Makefile       # [kernel 2.6]

$make all            # compile driver source code


But when I try this, the build command is missing as follows:


mypc@home:~/Desktop/rt61/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/home/adana/Desktop/rt61/RT61_Linux_STA_Drv1.0.4.0/Module modules
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory.  Stop.
make: *** [all] Error 2


Anyone have this problem?

---

### Post by diepruis on 2006-07-10
I don't think its make that's missing. If that was the problem the console output would have been something like "bash: make: command not found". I replied to your post in another thread, see if that works.

[Possible solution.]("http://ubuntuforums.org/showpost.php?p=1236018&postcount=12")

---

