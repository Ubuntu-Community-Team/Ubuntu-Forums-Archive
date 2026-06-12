---
title: "Places menu not working!"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sashin on 2011-03-13
Anyone else have a separate /home partition. I have this problem on two separate computers, one with a different /home hard drive and one with a different /home partition.

[http://oi53.tinypic.com/2m30184.jpg](http://oi53.tinypic.com/2m30184.jpg)

---

### Post by macroshaft on 2011-03-13
Working fine here

---

### Post by Harry33 on 2011-03-13
> **Sashin said:**
> Anyone else have a separate /home partition. I have this problem on two separate computers, one with a different /home hard drive and one with a different /home partition.

[http://oi53.tinypic.com/2m30184.jpg](http://oi53.tinypic.com/2m30184.jpg)

I have never encountered that kind of problem.
You might want to check from the file /etc/fstab that you have correct mounting configuration etc.

---

### Post by Sashin on 2011-03-13
I can access those files through nautilus, so Ima pretty sure its mounted, its just the menu that doesn't display anything.

---

### Post by Harry33 on 2011-03-13
> **Sashin said:**
> I can access those files through nautilus, so Ima pretty sure its mounted, its just the menu that doesn't display anything.

Might be a Unity issue.
Please check that with Gnome Classic session.

---

### Post by Sashin on 2011-03-13
Definitely a unity issue, the folders are all visible in the gnome-classic places menu.

---

### Post by macroshaft on 2011-03-13
> **Sashin said:**
> Definitely a unity issue, the folders are all visible in the gnome-classic places menu.

I had until very recently a problem where dash searches brought up applications twice, once in the applications section and again in the files search. My point being that even after the issue was resolved my copy of unity kept working this way until only a few days ago. You may find a re-install of the latest daily image would sort it.

---

### Post by libihero on 2011-03-13
i have the same problem, and i have my /home in a separate partition. when i choose the home folder in nautilus it shows it, but for some reason the button claims there is nothing in my home folder...

---

### Post by r-senior on 2011-03-13
Is your /home encrypted? Just a thought. Certainly a /home partition is fine here.

---

### Post by Sashin on 2011-03-13
No, it's not encrypted.

---

### Post by rburkartjo on 2011-03-13
i also have had the same problem for awhile.

---

### Post by nico1038 on 2011-03-13
I believe your problem is with zeitgeist (probably an update from a previous version). I would try this:

> rm -rf ~/.local/share/zeitgeist

---

### Post by Sashin on 2011-03-13
It worked!!!!!

---

### Post by libihero on 2011-03-13
me too!

---

