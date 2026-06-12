---
title: "How to erase history in Brasero?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by Manoboy on 2009-07-13
Use the Brasero in Ubuntu 8.10 to record CD and DVD, but every time I open the program at the bottom of the window appears "Choose a project recently opened," and just below the list of what has already been recorded.
I want to delete the list that appears. How do I find out?


Grateful.

---

### Post by vinutux on 2009-07-13
```
rm /home/[COLOR="Red"]yourusername[/COLOR]/.gconf/apps/brasero
```

then restart brasero

---

### Post by x33a on 2009-07-13
you can also clear the recent documents history from the places menu, and that'll remove brasero history too.

---

### Post by vinutux on 2009-07-13
> **x33a said:**
> you can also clear the recent documents history from the places menu, and that'll remove brasero history too.

Don't know...but think so

---

### Post by Manoboy on 2009-07-14
Unfortunately not had success with any of the methods, but one thing I noticed is that the Ubuntu 8.10 version of Brasero is 0.8.2 in Ubuntu 9.04 the version is 2.26.
Why this difference?

---

### Post by vinutux on 2009-07-14
> **Manoboy said:**
> Unfortunately not had success with any of the methods, but one thing I noticed is that the Ubuntu 8.10 version of Brasero is 0.8.2 in Ubuntu 9.04 the version is 2.26.
Why this difference?

not very diffrent...add some more features...nothing else

.

---

### Post by Manoboy on 2009-07-14
Now besides the problem described above, that solution still trying to find that Ubuntu does not recognize DVD+RW media.
Anybody know how to fix this?

---

### Post by x33a on 2009-07-14
you can give k3b a try
```
sudo aptitude install k3b
```

---

### Post by vinutux on 2009-07-15
> **x33a said:**
> you can give k3b a try
```
sudo aptitude install k3b
```


Yeh ...k3b is far better app....

anyway there is a linux version of popular NERO called **[NERO-LINUX]("www.nero.com/eng/linux3.html")**

is available in [official site]("www.nero.com/eng/linux3.html")...but its is trail-ware...you want to buy it for using more than 1 month.....
just try the trail-ware.......


.

---

### Post by emarkay on 2010-11-04
Years later, but as the OP asked, be advised that K3b has a not-easy-to-be cleared history:

[http://ubuntuforums.org/showthread.php?p=10070997#post10070997](http://ubuntuforums.org/showthread.php?p=10070997#post10070997)

---

### Post by jungle130 on 2013-03-29
[http://www.detector-pro.com/2009/04/how-to-remove-recent-projects-from.html](http://www.detector-pro.com/2009/04/how-to-remove-recent-projects-from.html)

works I tried it

"[LEFT][COLOR=#000000][FONT=Arial]Go to Places/Recent Documents and choose Clear Recent Documents. That’s it. Back in Brasero you will see that you recent projects are cleared. Now you can burn any files you want and after that remove your trails of curious eyes.[/FONT][/COLOR][/LEFT]"

---

### Post by coffeecat on 2013-03-29
Back to sleep, ancient thread.

---

