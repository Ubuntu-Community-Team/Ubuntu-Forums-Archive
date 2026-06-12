---
title: "Ubuntu 10.10 wont login"
date: 2010-07-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by su-37 on 2010-07-28
Thought id give the alpha 2 a spin. Upgraded perfectly. Re-started and takes me to the login window. I enter my password (which it doesn't reject) the screen goes away and then reappears asking for my password.
Any ideas?

---

### Post by Smart Viking on 2010-07-28
What happens if you log in at tty?

Maybe you could log in from there and then run startx. :)

---

### Post by su-37 on 2010-07-28
tty? Whats that? On the login screen i can choose xterm and others.

---

### Post by su-37 on 2010-07-28
Just entered the xterm one and it has come up with a terminal box. how do i run startx.

---

### Post by TheStroj on 2010-07-28
> **su-37 said:**
> tty? Whats that? On the login screen i can choose xterm and others.

just do a Ctrl + Alt + F1 to get into it

---

### Post by su-37 on 2010-07-28
And when i choose safe mode it lets me in. I tried to reset using start up manager.. Since i have chosen the safe mode i boots automatically into that.

---

### Post by Knatchwa on 2010-09-16
It's great to see this marked as solved yet I just started seeing this now with the most recent updates to 10.10 where I can login from terminal run startx, but it is the next step that is lacking. Is there a way to solve the loop I find myself in on a regular bootup. Is there something I am missing?

---

### Post by uRock on 2010-09-16
Moved to MM Testing and Discussion.

---

### Post by wilee-nilee on 2010-09-17
> **Knatchwa said:**
> It's great to see this marked as solved yet I just started seeing this now with the most recent updates to 10.10 where I can login from terminal run startx, but it is the next step that is lacking. Is there a way to solve the loop I find myself in on a regular bootup. Is there something I am missing?

I would start your own thread as one with solved on it is not helpful to you. 

A loop is unusual if it was me I would just back it up and reinstall, with a daily release.

---

### Post by Knatchwa on 2010-09-17
Well seems it was solved by running through some hoops, of starting in the recovery mode, using the terminal to start x - setting up nvidia using nvidia-xconfig and finishing it by restarting gdm, now I am seeing the desktop and all seems fine, so guess that makes this solved even for me. Thanks for the thoughts.

---

### Post by wilee-nilee on 2010-09-17
> **Knatchwa said:**
> Well seems it was solved by running through some hoops, of starting in the recovery mode, using the terminal to start x - setting up nvidia using nvidia-xconfig and finishing it by restarting gdm, now I am seeing the desktop and all seems fine, so guess that makes this solved even for me. Thanks for the thoughts.

Cool, there are few satisfactions better then figuring it out yourself.

---

