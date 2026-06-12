---
title: "Changed loginsound, can't login"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by Xantos on 2007-06-21
Hi all,

I changed the loginsound but after a restart I can't login anymore :(
I think the problem is, that I selected .wavfiles, which were in my home folder.

I don't get the welcome screen at all, I only get my cursor, which keeps on "turning"(like something is loading), at a black screen.

Does anyone know a command or so, so I can solve it? I have an exam webdesign tomorrow, and I  still would like to try out some stuff at my PC :p

Thnx

---

### Post by kevinlyfellow on 2007-06-21
hit ctrl-alt-f1 and login through the command line
enter ```
sudo /etc/init.d/gdm stop
```
Then ```
startx
```

---

### Post by Xantos on 2007-06-21
Thanks alot!

It works now:D
What I did:

> **kevinlyfellow said:**
> hit ctrl-alt-f1 and login through the command line
enter ```
sudo /etc/init.d/gdm stop
```
Then ```
startx
```
+
You can't edit the sounds cuz gdm is not on, so start up a terminal and type:
```
sudo /etc/init.d/gdm start
```

Then I did Alt+F2 (if it goes back to the black loginscreen) and tou adjust your sounds.

After this restart.

---

### Post by kevinlyfellow on 2007-06-21
Did you figure out what caused the problem?  Was it actually just choosing a sound in your home folder that cause it?

---

