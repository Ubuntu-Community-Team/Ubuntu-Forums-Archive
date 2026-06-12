---
title: "what is the new official way to install LAMP?"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by liorwohl on 2010-09-29
hello,
i installed the daily live cd today and its not include tasksel by default so i cant do
```
sudo tasksel install lamp-server
``` (and the synaptic "mark packages by task" too)

why there is no meta-package for LAMP with all the needed dependencies?

and what should i install to get apachi+mysql+php that work good without missing stuff?

thanks

---

### Post by liorwohl on 2010-09-29
oops i have found my answer too fast :)

there is an "invisable package" calld **lamp-server^ **(with the ^)
so:
```
sudo apt-get install lamp-server^
```

[http://superuser.com/questions/155448/ubuntu-10-04-lamp-installation](http://superuser.com/questions/155448/ubuntu-10-04-lamp-installation)

---

### Post by cariboo on 2010-09-29
tasksel is no longer installed by default, you have to manually install it.

---

### Post by liorwohl on 2010-09-29
tasksel is useless, meta-packages are better, but why there is no simple lamp-server package that you can find in USC?

---

### Post by cariboo on 2010-09-29
Tasksel works quite well with synaptic, or even from the command line, I've been using it for years for seting up servers. What's useless about it?

---

### Post by liorwohl on 2010-09-29
that it does exactly the same thing as a simple meta-package

---

### Post by Cenotaph on 2010-09-29
the difference is that deleting the task cleans the system better imo as it deletes all the packages of that task. meta-packages at most put them in autoremove, if you had  installed the packages manually before it wont even do that afaik. correct me if im wrong.

i always use tasksel to install lamp-server.

---

### Post by KamiOfTea on 2010-10-06
Is there a list of available/common meta-packages similar to the list provided when choosing to mark packages by task in synaptic provided by tasksel?

---

