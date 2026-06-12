---
title: "LAME question"
date: 2008-08-05
forum: Multimedia Software
---

### Post by underworld288 on 2008-08-05
Is there a way for you to use LAME to encode multiple files at a time? I tried to go into a folder with about 10 MP3 files and execute the following code...

```
lame -v --vbr-new *.mp3
```

... but nothing happened. It came back with this...

```
lame: excess arg nameoffile.mp3
```

Can anyone direct me to want I'm trying to achieve?

---

### Post by underworld288 on 2008-08-06
nevermind, I found a solution. I used the following...

```
find -type f -name '*.mp3' -exec lame -v --vbr-new '{}' \;
```

---

