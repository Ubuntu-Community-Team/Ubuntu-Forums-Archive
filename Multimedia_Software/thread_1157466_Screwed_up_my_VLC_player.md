---
title: "Screwed up my VLC player"
date: 2009-05-12
forum: Multimedia Software
---

### Post by redb on 2009-05-12
I tried to install a new skin and like a moron I put the wrong file into the box and clicked to install it.  Right now if I put a DVD in, the movie options will show up in a screen labeled media output.  The second I choose an title option it closes.  I have lost my skin so to speak.  

Is there anyway to fix this in terminal?  I don't have an option choice in the GUI.  

I've been looking and cant find anything about this.

---

### Post by mc4man on 2009-05-12
In a terminal

```
vlc --reset-config
```

---

### Post by lvleph on 2009-05-12
You could also edit the config file under .config/vlc

---

### Post by redb on 2009-05-12
> **mc4man said:**
> In a terminal

```
vlc --reset-config
```


Worked like a charm.  Thanks!

---

