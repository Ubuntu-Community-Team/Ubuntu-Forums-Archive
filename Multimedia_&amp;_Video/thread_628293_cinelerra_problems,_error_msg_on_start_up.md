---
title: "cinelerra problems, error msg on start up"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by beanco on 2007-12-01
when we start up cinelerra we get an error msg along the lines of


[PHP]void MWINDOW::init_shm(): WARNING: /proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff > /proc/sys/kernel/shmmax[/PHP]

we are n00bs and do not really undertand what this problem is and how to to the echo bit/

any tips/pointers?

thanks

robi and aron in Budapest

---

### Post by frymonster on 2008-01-02
I have the same error msg on start up and me knowing only a little of this sort of problem tried to run the 3rd line in the command prompt under a "sudo" but the command prompt only spat out unwanted banter of
"bash: /proc/sys/kernel/shmmax: Permission denied" 

I also need help with problem

---

### Post by frymonster on 2008-01-03
ok i figured it out all you have to do in enter a command prompt and put in ```
sudo su
```
enter your pass then type```
echo "0x7fffffff > /proc/sys/kernel/shmmax 
``` before starting up cinelerra

---

