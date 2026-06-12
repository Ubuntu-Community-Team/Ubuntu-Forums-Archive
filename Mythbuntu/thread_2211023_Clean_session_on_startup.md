---
title: "Clean session on startup"
date: 2014-03-13
forum: Mythbuntu
---

### Post by jim.hitch on 2014-03-13
Hi

I have the box unchecked to save session when I log out, and yet each time my backend starts, this lot opens up: two terminal windows, one editor window, one file manager window and one Alt-F4 run command window.

How can I clean this out so none of it opens on start up?

Many thanks.

---

### Post by TheFu on 2014-03-13
Don't know the answer you seek, but a workaround is to create a new userid.

---

### Post by steeldriver on 2014-03-13
Have you tried just deleting the contents of the ~/.cache/sessions directory?

---

### Post by jim.hitch on 2014-03-14
> **steeldriver said:**
> Have you tried just deleting the contents of the ~/.cache/sessions directory?

No, that was exactly the kind of answer I was looking for, thanks. I'll have a go this evening when I'm back home.

---

