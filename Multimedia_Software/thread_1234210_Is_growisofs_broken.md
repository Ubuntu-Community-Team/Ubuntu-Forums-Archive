---
title: "Is growisofs broken?"
date: 2009-08-07
forum: Multimedia Software
---

### Post by ohzopants on 2009-08-07
Since at least 8.04, I've been able to burn DVD+R DL disks just fine.  But recently it seems that growisofs craps out at a random point during the burn.

I know it's growisofs' fault because I typically use k3b which is just a front end for growisofs and I've used growisofs directly from the command line.

The errors aren't even consistent, I seem to get a different error every time, but they all include "Input/Output Error".

Any other type of media seems to work fine (except DVD-R DL, I just don't have any of those to test with).

Typically I rip my TV show DVDs to my pc and then use these disks to back them up on one disk so that I don't have to swap disks for different episodes (that really grinds my gears!).

I've tried burning the files using k3b but I get errors at different percentages (sometimes it gets 5% through the burn, others 95%) for the same set of files.  I've even tried making an .iso of the files and burning that but I get the same random errors!  I've tried different sets of files too, no luck!

It doesn't seem like growisofs has been updated in a while (it's provided in the dvd+rw-tools package), so I don't see how it could be a new bug.  Could a new kernel have caused this?

Has anyone else noticed similar behaviour?  And, even better, does someone have a fix?

---

### Post by finallyfound on 2012-07-22
necro'd because this post continues to appear in search results.


answer:
[http://ubuntuforums.org/showpost.php?p=9617383&postcount=17](http://ubuntuforums.org/showpost.php?p=9617383&postcount=17)
[http://ubuntuforums.org/showpost.php?p=9729294&postcount=23](http://ubuntuforums.org/showpost.php?p=9729294&postcount=23)

use of cdrtools PPA and hiding functional tools from still-broken gui

```
sudo add-apt-repository ppa:brandonsnider/cdrtools
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install cdrecord mkisofs
cd /usr/bin
sudo ln -s cdrecord wodim
sudo ln -s mkisofs genisoimage
```


Much the same wisdom as replacing sms with xmpp.  ;)

---

### Post by wildmanne39 on 2012-07-23
Thanks for sharing. Thread Closed.

---

