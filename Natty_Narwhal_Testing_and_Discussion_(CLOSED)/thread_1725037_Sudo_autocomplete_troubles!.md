---
title: "Sudo autocomplete troubles!"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by PatrickVogeli on 2011-04-09
Hi there,

I'm having troubles with the autocomplete feature. If I do it as my user, no problems, I can put gedit /et and it will autcomplete into gedit /etc/, but doing it as sudo, it behaves different. Instead of leaving me in the /etc/ dir, it autocompletes this way:
```

sudo gedit /etc 

```
Instead of entering the etc directory, I get a white space.

Using ubuntu classic, no desktop effects (compiz crashes a lot) and upgraded from Maverick.

Are you having this too?

---

### Post by ajgreeny on 2011-04-09
Try ```
gksudo gedit /etc
```and see if that helps.

You should never use sudo with GUI applications, but **gksu** or **gksudo** for gnome and **kdesu** for KDE.  See **Root sudo** link i my signature.

---

### Post by PatrickVogeli on 2011-04-09
yeah, I know, I'm not new into ubuntu.
 
Think of sudo cat /etc if that fits you better ;)

Anyway, gksudo gedit exhibits the same behaviour.

---

### Post by dino99 on 2011-04-09
for the lazy ones, like me, there is clicompanion (from ppa) that can be customized as you like (never had to type anything again, just pick into the list made)

---

### Post by MacUntu on 2011-04-09
In '/etc/bash_completion.d/acroread.sh' replace all '_filedir' with '_filedir_acroread'.

---

### Post by PatrickVogeli on 2011-04-09
mm the same happens :S

Actually, in that file, I only have 2 _filedir: one is the function name and the other in the _acroread function.

Thanks

---

