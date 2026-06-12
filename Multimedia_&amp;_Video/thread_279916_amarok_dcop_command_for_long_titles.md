---
title: "amarok dcop command for long titles"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by flapane on 2006-10-18
if I have a long author - title tag (on superkaramba with amarok) and I want to display author - title each one in a line (total two lines to fit the superkaramba window), how can I do?

[[IMG]http://img183.imageshack.us/img183/8336/sk31xf6.th.jpg[/IMG]](http://img183.imageshack.us/img183/8336/sk31xf6.jpg)

---

### Post by mitch.c on 2006-10-18
> **flapane said:**
> if I have a long author - title tag (on superkaramba with amarok) and I want to display author - title each one in a line (total two lines to fit the superkaramba window), how can I do?

I don't know much about superkaramba, but a simple cmd at the shell prompt could look like this:
```
user@ubuntu:~$ dcop amarok player nowPlaying | sed -e 's/ - /\n/'
```
Hope that helps.

---

### Post by flapane on 2006-10-19
you are great!!!
[[IMG]http://img96.imageshack.us/img96/6425/sk32iu9.th.jpg[/IMG]](http://img96.imageshack.us/img96/6425/sk32iu9.jpg)

---

