---
title: "Choppy videos"
date: 2009-10-13
forum: Multimedia Software
---

### Post by ToanTo on 2009-10-13
Hey everyone...I'm new to Ubuntu and just looking for some quick help so I don't mess up my desktop configuration

So a few days ago I had a problem where it would always run in low graphics mode...so since I didn't have much on the comp, I backed up my files and decided to install Ubuntu 8.04 instead of 9.14? (whichever the new one is)...Now it runs very nicely, only problem is when I play videos, it is very choppy unless the video screen is reduced to like 2 inches.  I'm thinking it has to do with my graphics card?  Before, when I had the other version of ubuntu prior to the low graphics mode deal, videos would play flawlessly.  

Any suggestions?

---

### Post by wojox on 2009-10-13
Open a terminal and post back the results of this command:

```
lspci | grep VGA
```

---

### Post by ToanTo on 2009-10-13
Here's what I got:

02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

