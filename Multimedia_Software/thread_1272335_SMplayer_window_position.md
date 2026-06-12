---
title: "SMplayer window position"
date: 2009-09-22
forum: Multimedia Software
---

### Post by jackallen0714 on 2009-09-22
It's weired that every time I pause a movie, the window of SMplayer will jump a little toward the bottom of workplace, accompany with a quick disappearing of the window. Any one know why and how to fix it ? :confused:

---

### Post by rvm4000 on 2009-09-22
Maybe you have the option **Video -> Stay on top -> While playing** enabled.

Select Always or Never instead.

---

### Post by jackallen0714 on 2009-09-22
> **rvm4000 said:**
> Maybe you have the option **Video -> Stay on top -> While playing** enabled.

Select Always or Never instead.

It works! THX !

Is it a bug? Totem has similar option but never behaves like this ...

---

### Post by vinutux on 2009-09-22
> **jackallen0714 said:**
> It works! THX !

Is it a bug? Totem has similar option but never behaves like this ...

plz...mark post solved....(under thread tool)

---

### Post by rvm4000 on 2009-09-23
> **jackallen0714 said:**
> Is it a bug? Totem has similar option but never behaves like this ...

In any case it would be a bug or limitation of the Qt library. The function to change the window flags hides the window... smplayer makes it visible again and places it in the same position where it was before. If the window actually moves to the bottom, it might be a problem of the window manager.

---

### Post by diversario on 2012-08-19
I'm sorry, but why is this marked [SOLVED] when SMPlayer still does this? Is this an expected behaviour or maybe it is out of developer's control?

D'oh! rvm4000 is the developer. So, it this bug/limitation still there, I assume?

---

### Post by wildmanne39 on 2012-08-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

