---
title: "Cheese Webcam Booth Multi Burst Question"
date: 2010-09-09
forum: Multimedia Software
---

### Post by c0stalkayk3r on 2010-09-09
Hello,

I am running Cheese 2.30.1 on Ubuntu 10.04. I am trying to do some time lapse photos, and have found the "Burst Mode" and the settings. My question is: Is there a way to change the default maximum for the **Delay between Photos [seconds]**? It currently maxes out at 100 seconds and I would like it to be capable of a delay of 3600 seconds (1 hr). Any ideas?

Thanks,

Kurt

---

### Post by ost2life on 2010-12-06
it's a bug and the explaination on how to fix it is [here]("http://yuvi.in/blog/how-to-increase-cheese-s-burst-mode-photo-count.html")

I'm going to copy it here though.
first
```
gksudo gedit /usr/share/cheese/cheese-prefs.ui
```

in the gedit window go to line 8 and adjust the value to whatever you want, and then do the same in line 13. Save, close, restart Cheese and in the preferences dialog you should be able to set whatever value you want.

---

### Post by azertyh on 2010-12-06
hello,
i didn't notice that the max is 100 seconds.
thanks to share this.

---

