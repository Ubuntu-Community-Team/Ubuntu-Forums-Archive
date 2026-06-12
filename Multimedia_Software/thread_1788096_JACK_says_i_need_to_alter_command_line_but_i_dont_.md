---
title: "JACK says i need to alter command line but i dont know how"
date: 2011-06-22
forum: Multimedia Software
---

### Post by stephenstop on 2011-06-22
p, li { white-space: pre-wrap; } rtain conditions; see the file COPYING for details
 [COLOR=#999999]01:40:01.462 JACK was started with PID=3523.[/COLOR]
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1540092


can someoneplease please tell medo i need to do this and if so how?

---

### Post by kayosiii on 2011-06-22
Ardour likes lots of memory. I am reasonably certain you can ignore that warning message. Otherwise check the file /etc/security/limits or perhaps /etc/security/limits.d/audio
and change the line unlimited to a number that is less than the amount of physical ram in the system.

---

### Post by stephenstop on 2011-06-22
how do i find out how much ram?and how do i change that file?

---

### Post by Yellow Pasque on 2011-06-22
I wouldn't touch it unless I saw a performance drop and free -m showed heavy swap use: [http://www.frontlinemedia.org.au/node/54](http://www.frontlinemedia.org.au/node/54)
How do you edit a file with root permissions?
```
gksu gedit <file(s)>
```

---

### Post by stephenstop on 2011-06-22
thank you so so so much for responding im going crazy here,so why does it say that?i have like a million x-runs and i found a li/

limits.conf  and /limits.conf2 under ect/security their is a limitts .conf is this normal?

---

### Post by Yellow Pasque on 2011-06-22
The warning is there in case you don't have enough virtual memory to do a certain task, which is a possibility on low/mid-range systems. How much RAM and swap do you have? In other words:
```
free -m
```

---

### Post by stephenstop on 2011-06-22
hey thanks again for the help,im way behind when it comes to everything.got Lyme disease and that knocked me outta comission for awhile
[/CODE]
owner@owner-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005        444       1560          0         38        224
-/+ buffers/cache:        180       1824
Swap:         1609          0       1609[CODE]

---

### Post by stephenstop on 2011-06-22
```

```  
                  total      used        free     shared    buffers     cached
Mem:          2005        444       1560          0         38        224
-/+ buffers/cache:        180      1824
Swap:         1609          0         1609
```

```

---

### Post by Yellow Pasque on 2011-06-22
So you have 2GB of RAM and your system doesn't use a whole lot on its own. That's fine.

---

### Post by stephenstop on 2011-06-22
Ok thank you i appreciate it,so it doesnt matter if their are at least 2 files that have that configuration about unlimited memory or watever?
Also i have serious runs.....x-runs...thats a terrible joke...could ya give me somehints there

---

