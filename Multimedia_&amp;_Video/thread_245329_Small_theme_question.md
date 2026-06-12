---
title: "Small theme question"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by jISh on 2006-08-27
I have downloaded a GTK theme that I really like, however the OpenOffice and Firefox menu bar texts are black instead of white as in other applications. Does anybody know how to fix this?

---

### Post by mynimal on 2006-08-27
> **jISh said:**
> I have downloaded a GTK theme that I really like, however the OpenOffice and Firefox menu bar texts are black instead of white as in other applications. Does anybody know how to fix this?
In Firefox, add

```

menu {
    color: #FFF;
}
```

to ~/.mozilla/firefox/(profile)/chrome/userChrome.css. Don't know about OpenOffice.

---

