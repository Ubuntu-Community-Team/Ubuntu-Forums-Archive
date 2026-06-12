---
title: "USR help"
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by James_M on 2005-12-20
Hi everyone, This is my first post, so bear with me, please.
Anywho...I have a US Robotics ethernet card (USR997901A) and the instructions on the CD are so vague, I have no clue what's going on.  The three files are a makefile, the instruction sheet (txt) and a file labeled usr.c

I tried using the "make" command, but terminal doesn't like it and nothing happens.    Can anyone help me out, because I can't get anything out of the provided instructions.  Thanks.

---

### Post by invalid on 2005-12-20
> but terminal doesn't like it and nothing happens
Can you a bit more specific? Can you paste the *exact* command and output?

---

### Post by James_M on 2005-12-20
[QUOTE=invalid]Can you a bit more specific? Can you paste the *exact* command and output?[/QUOTE]
```
bash: make: command not found
```  This is after attempting to modify the makefile.

---

### Post by invalid on 2005-12-20
```
sudo apt-get install build-essential
```

---

### Post by James_M on 2005-12-20
now what?  It looks like it installed something with command line.

---

### Post by invalid on 2005-12-21
Now try make again. It installed some essentials for building and compiling packages, including the make command.

---

