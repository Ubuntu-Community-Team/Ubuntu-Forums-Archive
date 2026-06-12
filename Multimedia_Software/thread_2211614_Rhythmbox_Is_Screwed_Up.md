---
title: "Rhythmbox Is Screwed Up"
date: 2014-03-16
forum: Multimedia Software
---

### Post by douglas3 on 2014-03-16
Rhythmbox on 13.10 won't start or run the right way, and I have to mess around with the controls to get it to play a cd between crashes, then it only plays one song at a time. Should I reinstall it or install an alternative, and, if so, how?

---

### Post by Kirboosy on 2014-03-17
Welcome to the forums!

Have you made any changes to Rhythmbox lately? Updates etc? 

You might want to try resetting Rhythmbox back to default settings (like you have never used it)

Make sure you have the program completely closed before you run this command! From a terminal if you type in the following command it should reset everything.

```
rm -r ~/.local/share/rhythmbox/ ~/.cache/rhythmbox/ ~/.gconf/apps/rhythmbox/
```

Hope that helps!
~Caboose

---

### Post by tgalati4 on 2014-03-17
Run *rhythmbox* in a terminal and post any helpful messages.

---

