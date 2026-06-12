---
title: "[SOLVED] amarok - ratings stored where?"
date: 2008-08-11
forum: Multimedia Software
---

### Post by JohnDorian on 2008-08-11
When i rate a song in Amarok, I don't believe it tags the file with it.  Rather I think its saved in a different location.  I had to do a fresh install of ubuntu b/c I mucked things up trying Kubuntu.  I have backups of everything but given how mangled things were I want to selectively back things up.  

So short version is - anyone know where I should look to find where Amarok stores its song ratings?

thanks

---

### Post by JohnDorian on 2008-08-14
*bimp*

---

### Post by cariboo on 2008-08-14
Have you looked in:

```
~/.kde/share/apps/amarok
```

Jim

---

### Post by JohnDorian on 2008-08-17
I hadn't.   I'm still trying to de-windows-ize myself and the location of such data is a big challenge for me.  

I asked on launchpad and got the following answeer, which took care of this.

~/.kde/share/apps/amarok/collection.db

---

