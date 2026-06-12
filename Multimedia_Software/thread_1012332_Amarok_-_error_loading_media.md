---
title: "Amarok - error loading media"
date: 2008-12-15
forum: Multimedia Software
---

### Post by terry@softreq.com on 2008-12-15
n/a

---

### Post by skern03 on 2008-12-31
> **terry@softreq.com said:**
> I tried listening to a radio stream using Amarok (just loaded Ubuntu 8.10) and got the error
"error loading media -  no suitable input plugin..." 

Not sure what to do. 

Any help would be appreciated.

Thanks, Terry

Amarok worked fine in 8.04, but when I upgraded to 8.10, I got the same error. I found a fix here:

[http://ubuntuforums.org/showpost.php?p=6096148&postcount=2](http://ubuntuforums.org/showpost.php?p=6096148&postcount=2)

Basically, in a terminal, you type "sudo apt-get install libxine1-ffmpeg" and it loads libraries that aren't brought over in 8.10.

---

