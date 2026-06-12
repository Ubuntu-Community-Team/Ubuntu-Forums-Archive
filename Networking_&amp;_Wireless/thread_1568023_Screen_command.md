---
title: "Screen command"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by pedram@patexia.com on 2010-09-04
I am trying to run a script remotely and would like to let it run while I close the terminal window or perhaps turn off the local machine. I know screen is probably the right command to use but not sure how to use it.

Basically I would like to turn off the local machine or close the terminal but be able to go back and re-open the same terminal to check the status of the program running.

---

### Post by scorp123 on 2010-09-04
> **pedram@patexia.com said:**
>  I know screen is probably the right command It is :D

> **pedram@patexia.com said:**
> but not sure how to use it. Read here:

[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

### Post by clrg on 2010-09-04
No need for screen. Use nohup: 
```
nohup myscript.sh &
```
That will start myscript.sh and run it in the background. nohup will create a file nohup.out in the current directory and write all output of myscript.sh there. 

So if you log off, myscript.sh will continue to run. When you log back in again and want to check the progress, just look at nohup.out:
```
tail -f nohup.out
```

Of course this works for other programs too, not just scripts.

---

### Post by pedram@patexia.com on 2010-09-04
> **clrg said:**
> No need for screen. Use nohup: 
```
nohup myscript.sh &
```
That will start myscript.sh and run it in the background. nohup will create a file nohup.out in the current directory and write all output of myscript.sh there. 

So if you log off, myscript.sh will continue to run. When you log back in again and want to check the progress, just look at nohup.out:
```
tail -f nohup.out
```

Of course this works for other programs too, not just scripts.

Thank you. This works exactly as I wanted.

---

### Post by Baji P. on 2010-09-04
```
screen -d -m
```
if you man screen :
-d -m   Start screen in "detached" mode. This creates a new session but doesn't attach to it. This is useful for system startup scripts.

---

