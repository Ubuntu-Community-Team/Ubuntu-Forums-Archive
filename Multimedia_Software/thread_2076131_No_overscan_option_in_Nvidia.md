---
title: "No overscan option in Nvidia"
date: 2012-10-25
forum: Multimedia Software
---

### Post by williammanda on 2012-10-25
I was upgrading my systems to 12.10 and the first of two systems that use the overscan option in Nvidia, wasn't there in the available Nvidia versions. I have come to depend upon the overscan option since neither tv has the ability to correct this...one is a crt tv. What options do I have to get the overscan option back? I realize I can go back to 12.04...which I may do.
Thanks

---

### Post by williammanda on 2012-10-26
anyone?

---

### Post by pudgewack on 2012-10-26
I too have this same issue.  Hopefully we can find a fix soon.

Matt

---

### Post by pudgewack on 2012-10-26
I found a work around.  It is not as easy as in nvidia x-server Settings, but it does work.  

I found the info here:
[[SOLVED] New Nvidia driver - no overscan compensation?]("http://www.pclinuxos.com/forum/index.php?topic=106650.0")


In summary:

Try this command:
```
nvidia-settings --assign 0/CurrentMetaMode="DFP-1: 1920x1080 { ViewPortOut=1840x1030+40+25 }"
```

I had to change the ViewPortOut numbers for a better fit on my TV.

Once you get the numbers that work best for you, can place in the info info your xorg.conf file.

There are more details in link I posted.

Good luck!

Matt

---

### Post by williammanda on 2012-11-03
Thanks for the info! I did use this but it does take some tweaking.

---

