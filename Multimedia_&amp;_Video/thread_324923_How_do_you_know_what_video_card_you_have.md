---
title: "How do you know what video card you have?"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by jenigmat429 on 2006-12-24
Yeah, I was wondering how to tell what video card one had.

---

### Post by taurus on 2006-12-24
Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by cilynx on 2006-12-24
```
lspci | grep -i vga
```
is usually pretty good

---

