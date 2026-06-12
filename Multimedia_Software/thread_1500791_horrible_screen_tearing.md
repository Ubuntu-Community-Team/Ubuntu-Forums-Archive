---
title: "horrible screen tearing?"
date: 2010-06-03
forum: Multimedia Software
---

### Post by insanity99 on 2010-06-03
i have a radeon HD4870 and use the proprietary drivers, i also but windows manager on metacity put the screen tearing while watching videos is unbearable, is there anything i can do?

---

### Post by insanity99 on 2010-06-03
bump

---

### Post by rizzeh on 2010-06-03
nvidia video drivers have Vsync for video playback option, it usually helps with tearing, have a look in ati drivers for a similar option.

---

### Post by insanity99 on 2010-06-03
all i can see is V-Sync for 3D apps.

---

### Post by rizzeh on 2010-06-03
have you tried this?
```
sudo aticonfig --sync-video=on
```

---

### Post by insanity99 on 2010-06-04
sorry i really suck with terminal currently, i am reading a book now though.

i got this error


neil@neil-desktop:~$ sudo aticonfig --sync-video=on
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.
neil@neil-desktop:~$ aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections
neil@neil-desktop:~$

---

### Post by rizzeh on 2010-06-04
i haven't got an ati card to test out commands, try  
```
sudo aticonfig --initial -f
```

---

### Post by sixstringmonk on 2010-06-04
I've got this issue too with a 5850. It seems like vsync is off on 2d rendering. I've successfully run both console commands mentioned in this thread, but it did not fix the problem.

---

### Post by rizzeh on 2010-06-04
sorry, without ati card i can't test much, but quick google search brings few hits -like [this]("http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-ati-vsync-video-tearing-issue-once-and-for-all/"):```
sudo aticonfig –sync-video=on –vs=on
```

  personally i buy nvidia cards only cuz thier drivers in linux are good... or errm, better than ati's... not perfect though.

---

### Post by emergence on 2010-06-05
It seems VSync is off in the catalyst drivers. This looks like a bug! I'm also experiencing tearing with HD5850.

Here's something you can try:
In compiz setting manager, enable the benchmark plugin and uncheck "Disable limiter". Does that fix tearing? It did for me. Of course, I don't want a benchmarking tool running all the time... but proves that VSync is not working.

---

### Post by insanity99 on 2010-06-05
> **emergence said:**
> It seems VSync is off in the catalyst drivers. This looks like a bug! I'm also experiencing tearing with HD5850.

Here's something you can try:
In compiz setting manager, enable the benchmark plugin and uncheck "Disable limiter". Does that fix tearing? It did for me. Of course, I don't want a benchmarking tool running all the time... but proves that VSync is not working.


hey that did fix it thanks, only problem is theres a huge FPS counter in the way of the videos, is there a way to disable this? then im all set.

---

### Post by emergence on 2010-06-05
Yes, in the same window, uncheck Enable under Screen Output. But you really don't want to do this. I don't want to do this.

What does this tell us about the issue?

Who is responsible to fix this? Ubuntu, Compiz, ATI?

Is there another option we can play with to perform the same effect?

VSync in the ATI settings and in the Compiz settings do not help... Someone please help us!

---

### Post by insanity99 on 2010-06-05
it's a real annoyance, i just managed to convince my brother linux is better than windows when he realises he cant even watch videos because the screen tearing is so awful.

i dont care whose fault it is but this is holding Linux back a lot and needs to be fixed

---

### Post by robincawser on 2010-07-22
> **emergence said:**
> 
Who is responsible to fix this? Ubuntu, Compiz, ATI?

Is there another option we can play with to perform the same effect?

VSync in the ATI settings and in the Compiz settings do not help... Someone please help us!

I want to bring this thread back to life. I have a 5850 and ubuntu is suffering from tearing on the desktop and in videos.

Surely if we can get vsync working using CCSM by enabling benchmarking then there must be a setting/ conf file that we could change to enable vsync *all the time*?

Maybe the next ati driver will sort us out.

---

### Post by step5 on 2010-08-26
still same effect here using catalyst 10.8 driver

must be a compiz bug

i'm not the best in searching bugtrackers, maybe there's a bug report for this problem already // if not may some kind sir put one up :)

---

### Post by step5 on 2010-08-26
...

---

### Post by gonintendo on 2010-10-12
bump. same problem with my 5850 on 10.10

---

### Post by Azazel on 2010-10-24
> **gonintendo said:**
> bump. same problem with my 5850 on 10.10

Ubuntu 10.10 or Catalyst 10.10?

I have the FGLRX drivers installed from repositories and am downloading CCC 10.10 from AMD right now to see if it helps

---

### Post by SeePU on 2010-10-24
> **Azazel said:**
> Ubuntu 10.10 or Catalyst 10.10?

I have the FGLRX drivers installed from repositories and am downloading CCC 10.10 from AMD right now to see if it helpsDoes it?  CCC 10.10 on Ubuntu Maverick 10.10 is supposed to be improved or so I've been told (and read).

Of course, you can't use xv-video output yet or there's tearing.  You need v-sync on, I think. 

Test on:  VLC, MPlayer, Kaffeine.... see if there's any differences in performance/output.

---

