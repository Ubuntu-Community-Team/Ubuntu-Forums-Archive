---
title: "Unity Desktop problem"
date: 2011-03-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2011-03-16
When I switch to unity desktop, I have no panel and no sidebar just the desktop menu.

I have compiz enabled on ubuntu classic desktop.

---

### Post by cariboo on 2011-03-16
Can open a terminal by pressing Ctrl-Alt-t, then type:

```
unity --reset
```

---

### Post by tad1073 on 2011-03-17
> **cariboo907 said:**
> Can open a terminal by pressing Ctrl-Alt-t, then type:

```
unity --reset
```

While in Unity Desktop Environment?

---

### Post by VMC on 2011-03-17
> **tad1073 said:**
> When I switch to unity desktop, I have no panel and no sidebar just the desktop menu.

I have compiz enabled on ubuntu classic desktop.

I've had that situation a few times. If I use a virtual terminal, sometimes I have problems - fatal errors trying to restart compiz.

What I now have on my desktop is two executable files that either run "compiz --replace", the other "unity --reset". then I just double-click and the sidebar comes back.

The reason I do that is because when I have no sidebar, I only have mouse commands. Keyboard doesn't work.

---

### Post by tad1073 on 2011-03-18
I got Unity Desktop back with that command, thanks.

@VMC I will have to try your suggestion.

---

