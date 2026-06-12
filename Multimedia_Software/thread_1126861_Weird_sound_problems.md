---
title: "Weird sound problems"
date: 2009-04-15
forum: Multimedia Software
---

### Post by Roanoke on 2009-04-15
When I tried to use espeak today, the following error resulted.
```

$ espeak
heh
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
^C

```
'heh' is, of course, what I tried to synthesize (a test). Why did this happen? Other sounds play fine.

---

