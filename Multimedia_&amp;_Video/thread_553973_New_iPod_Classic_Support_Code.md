---
title: "New iPod Classic Support Code"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by Ladybug_309 on 2007-09-18
So, when I found out that the new iPod had finally been cracked, I was super excited & went to this page - [http://www.backdot.com/?p=50](http://www.backdot.com/?p=50) - to see if I could make it work.

I should note that I'm relatively new to Ubuntu, but I'm having a couple of issues.

1. I don't know what he means in step 3 by "run make to compile the hash file" 
2. I went ahead & skipped to step 4/5 to the "./gethash" command, but when I run that in Terminal, it tells me that "bash ./gethash no such file or directory"

Any suggestions?  Or should I just hold off until the new code is integrated into gtkpod/Amarok et. al?

---

### Post by nwcowboysfan on 2007-09-19
> **Ladybug_309 said:**
> So, when I found out that the new iPod had finally been cracked, I was super excited & went to this page - [http://www.backdot.com/?p=50](http://www.backdot.com/?p=50) - to see if I could make it work.

I should note that I'm relatively new to Ubuntu, but I'm having a couple of issues.

1. I don't know what he means in step 3 by "run make to compile the hash file" 
2. I went ahead & skipped to step 4/5 to the "./gethash" command, but when I run that in Terminal, it tells me that "bash ./gethash no such file or directory"

Any suggestions?  Or should I just hold off until the new code is integrated into gtkpod/Amarok et. al?

For step 3, just change to the directory were you unzipped the source code and type "sudo make". This will create the exeucatble gethash. Then you can follow the remaining steps. I tried this procedure with an 80G classic, but it still did not work. Hopefully it will work for you or there will be an official fix soon.

---

