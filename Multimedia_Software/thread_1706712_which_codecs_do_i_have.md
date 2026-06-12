---
title: "which codecs do i have?"
date: 2011-03-14
forum: Multimedia Software
---

### Post by pdro7 on 2011-03-14
hi, i'm using ffmpeg and i'd like to know what codecs i have installed on my system. how can i know that?
thanks

---

### Post by cipherboy_loc on 2011-03-14
```

ffmpeg -codecs

```

Worked for me. But be warned, it gives you a lot of output (at least on my system).



Cipherboy

---

### Post by Paddy Landau on 2011-04-01
I find -codecs gives an error. This worked for me:
```
ffmpeg -formats
```

---

