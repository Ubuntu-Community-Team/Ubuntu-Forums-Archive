---
title: "Brasero won't launch"
date: 2011-03-25
forum: Multimedia Software
---

### Post by steaksauce on 2011-03-25
Okay, so I've been burning a few linux ISOs lately to play around on a desktop I have (archlinux, Fedora, etc) and a few days ago Brasero stopped launching. I tried to uninstall/reinstall Brasero, but it still didn't work. There we no error messages, it would just try to start up, and quit.

I got frustrated and tried to run Brasero from the command line and got this:```

user@computer:~$ brasero
Bus Error
user@computer:~$

```Is there a way to fix this?

---

### Post by drs305 on 2011-03-25
You could try 'purging' brasero to remove all its files/settings. Purging is sometimes a bit more comprehensive, depending how you removed it. This may restore it.

```
sudo apt-get purge brasero && sudo apt-get install brasero
```

---

### Post by steaksauce on 2011-03-25
> **drs305 said:**
> You could try 'purging' brasero to remove all its files/settings. Purging is sometimes a bit more comprehensive, depending how you removed it. This may restore it.

```
sudo purge brasero && sudo apt-get install brasero
```

```
user@computer:~$ sudo purge brasero
[sudo] password for user: 
sudo: purge: command not found
```

---

### Post by steaksauce on 2011-03-25
I guessed a command and
```

sudo apt-get purge brasero

```
and then reinstalled using apt-get and when I launch, I still get bus error

---

### Post by drs305 on 2011-03-25
> **steaksauce said:**
> I guessed a command and
```

sudo apt-get purge brasero

```
and then reinstalled using apt-get and when I launch, I still get bus error

I'm glad you figured out the part of the command I dropped. Sorry it didn't help. Hopefully someone else will post offering further advice.

I'll edit my previous post to correct the error should someone else try to use it.

---

