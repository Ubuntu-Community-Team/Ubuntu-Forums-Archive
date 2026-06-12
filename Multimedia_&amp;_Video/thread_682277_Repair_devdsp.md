---
title: "Repair /dev/dsp"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by karusho on 2008-01-29
Okay, I've been having problems with /dev/dsp.

At least two of my programs trying to use it have failed.  Both worked before.  Is there anyway to reset /dev/dsp to original installation?  Or am I thinking on the wrong track?

My main problem is espeak produces this:

```
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

---

### Post by Yellow Pasque on 2008-01-29
Well, what does it point to?
```
cd /dev;  ls -l | grep dsp
```

---

### Post by karusho on 2008-02-05
I get this:
```

crw-rw---- 1 root   audio      14,   3 2008-02-04 22:14 dsp

```

---

