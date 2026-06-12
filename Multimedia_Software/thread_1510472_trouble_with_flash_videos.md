---
title: "trouble with flash videos"
date: 2010-06-15
forum: Multimedia Software
---

### Post by dizzy1kenobi on 2010-06-15
Why cant I interact with google videos embedded in websites?

---

### Post by lovinglinux on 2010-06-16
I suppose you are using 64bit Ubuntu and browser.

Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by dizzy1kenobi on 2010-06-19
That worked perfectly.

Thank you.

---

