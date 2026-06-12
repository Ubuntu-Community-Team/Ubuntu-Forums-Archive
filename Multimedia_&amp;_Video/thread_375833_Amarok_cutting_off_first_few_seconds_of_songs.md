---
title: "Amarok cutting off first few seconds of songs"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by tisk on 2007-03-04
I'm using gnome and trying to get amarok set up successfully. everything works fine, except sometimes amarok seems to cut off the first few seconds of a song.
has anyone else experienced this problem/ found a fix?

---

### Post by zoryn on 2007-03-09
I can confirm it. if you turn the crossfade on, it doesn't cut. Try putting it only on "manual track change only", and it won't cut the beginning anymore. It will crossfade on manual track change though... I searched for help for this once, but to no one answered, so I guess it only happens to a few people, or there's no solution.

---

### Post by tisk on 2007-03-11
yeh, your right, it's crossfading that's the problem. This is obviously a bug. 
crossfading only on manual changes seems a good temporary fix. :)

---

### Post by zoryn on 2007-03-11
try opening up a bug report in launchpad...

---

### Post by lemboy4 on 2008-01-12
So, this thread is way old, but I have the latest version of Amarok from the Ubuntu repositories and I am seeing this same behavior.

Has a bug report been posted, or should I do that?

---

### Post by tisk on 2008-01-12
I haven't reported a bug, although I would be interested to know if anyone using kde has the problem.

---

### Post by prasadz8 on 2008-01-13
Hi. I'm running on Gutsy and have been using amarok for quite a while now. Lately, after installing Ubuntu Studio, I've noticed that Amarok only plays a song for only about 30 seconds. Then, it just stops responding. Why is this happening?

Things get worse, I can't start Amarok again after its forced to quit. Opening Amarok in the terminal after a 'force-quit' gives a blank line with no response or what so ever. A CTRL+C breaks the pause.

-------------
Terminal:
-------------
                         line00: praz@PrazStudio:~$ amarok
*no response *    line01: 
*[CTRL+C] *         line02: praz@PrazStudio:~$ 

--------------
 I love Amarok...why is she doing this to me?
Any solutions to this one? Maybe on of ubuntu studio's installed software is clashing?

---

### Post by tisk on 2008-01-13
firstly I would put this in a different thread since I don't think the issues are related. 

Have you tried running amarok from the terminal with extra verbosity? i.e.
```
 amarok -v
```

this might tell us more...
I don't have any experience with ubuntu studio so I don't know what possible conflicts there would be there.  You could try using a different engine within amarok and seeing what happens. What engine are you using?

---

### Post by prasadz8 on 2008-01-14
> **tisk said:**
> firstly I would put this in a different thread since I don't think the issues are related. 

Have you tried running amarok from the terminal with extra verbosity? i.e.
```
 amarok -v
```

this might tell us more...
I don't have any experience with ubuntu studio so I don't know what possible conflicts there would be there.  You could try using a different engine within amarok and seeing what happens. What engine are you using?

--i'm using the Xine engine. How do i get more engines?
on terminal:
------------------
praz@PrazStudio:~$ amarok -v
Qt: 3.3.7
KDE: 3.5.8
Amarok: 1.4.8
praz@PrazStudio:~$ 

The issue of restarting amarok was dealt with by opening the System Monitor and manually terminating the process. But the problem still persists.

p.s. - how do we start a new thread?  [noobie here]

---

### Post by prasadz8 on 2008-01-14
Eureka!

```
amarok --engine Xine
```This solved the problem. For now. [-o<

---

### Post by SirBedevere35 on 2008-05-23
> **tisk said:**
> I haven't reported a bug, although I would be interested to know if anyone using kde has the problem.

I have exactly the same problem. It is VERY annoying. And using the crossfading on manual changes only does not work either :-(

anyone here has a solution ?

---

