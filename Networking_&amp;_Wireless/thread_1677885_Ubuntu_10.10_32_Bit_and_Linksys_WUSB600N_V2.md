---
title: "Ubuntu 10.10 32 Bit and Linksys WUSB600N V2"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by theprez on 2011-01-29
Hello,

I just recently installed Ubuntu 10.10 and am fairly new to Unix.  I've noticed that the Linksys WUSB600N v2 wireless was not detected automatically.  

if I do a "lsusb" I see that it was recognized but I don't understand why the driver isn't loading.

Any ideas?

PS - as a last resort, I hardwired my computer to ethernet and did an update but it still didn't find my wireless USB adapter.

Thanks!

---

### Post by Spartako on 2011-01-29
Try this:
[http://art.ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://art.ubuntuforums.org/showpost.php?p=8591348&postcount=6)

You just have to change the  ID **1737:0078**  with the ID that "lsusb" reports.

---

### Post by theprez on 2011-01-29
That didn't work but thanks for the suggestion.

Anything else?

---

