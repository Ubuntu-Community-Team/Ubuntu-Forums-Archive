---
title: "Saytime give error &quot;sox formats: no handler for given file type `ossdsp' &quot;"
date: 2009-09-26
forum: Multimedia Software
---

### Post by shredder12 on 2009-09-26
I just installed saytime and when i tried to run it, i got the following error..

```
sox formats: no handler for given file type `ossdsp'
child process returned a non-zero status 2
```

Any fix for this problem???

---

### Post by shredder12 on 2009-09-27
Even though I fixed this problem by installing a sox library that handles oss file..
libsox-fmt-oss..
but now I am getting this error

```
sox formats: can't open output file `/dev/audio': Device or resource busy

```

any suggestions....

---

### Post by shredder12 on 2009-09-27
When I read man saytime.. I found that i have an option to change the output file.. (default is /dev/audio)..
so is there any other file.. which I can use...

or is it possible to use such devices  multiple times..

---

