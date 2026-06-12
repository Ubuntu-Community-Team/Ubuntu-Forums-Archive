---
title: "Skype audio"
date: 2011-04-04
forum: Multimedia Software
---

### Post by rvchari on 2011-04-04
skype was functioning perfectly well... off late (i know i was fiddling with something in sound preferences which i cant recollect) after which my voice cant be heard by others on the other side

do i have to reconfigure my audio ? if so then i need help !

---

### Post by shantiq on 2011-04-05
HI rvchari first stop   preferences/sound     make sure your input and output are correct


if that is not enough

```
sudo apt-get install gnome-alsamixer 

```


then make sure everything is enabled that you want enabled (if not sure enable everything)



you can do the same through pavucontrol too

```
sudo apt-get install pavucontrol
```



Hope this helps and works for you

---

### Post by rvchari on 2011-04-05
thankx guys...
i had to uninstall and re install drivers...
wonder y skype plays havoc at times...
as of now sound is back.

---

