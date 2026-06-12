---
title: "Guayadeque crashes after playing a while"
date: 2011-09-12
forum: Multimedia Software
---

### Post by ravisghosh on 2011-09-12
I tried this music player called Guayadeque (there aren't many good options after Amarok 1.4, gmusicbrowser is one). However, after playing a song or two, it would crash. I started it from terminal and this is the error that I got.


> 7ffa5d592000-7ffa5d593000 rw-p 00063000 08:02 14384                      /usr/lib/libsndfile.so.1.0.23Aborted


Anybody knows how to fix it?

---

### Post by dniMretsaM on 2011-09-12
I don't know how to fix your problem, but you might be interested in the Clementine music player. It's a nice fork of Amarok 1.4. It would, in a way, fix your problem since you wouldn't be needing to use Guayadeque.

---

### Post by anonbeat on 2011-09-12
> **ravisghosh said:**
> I tried this music player called Guayadeque (there aren't many good options after Amarok 1.4, gmusicbrowser is one). However, after playing a song or two, it would crash. I started it from terminal and this is the error that I got.




Anybody knows how to fix it?

Are you using the latest version from my ppa ? you can try with

```
sudo apt-get remove guayadeque
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```

If after that you continue with segfaluts please go to guayadeque.org and report the problem to help you

Thanks

---

### Post by AmsterdamMack on 2011-10-24
Thank's that solved it for me on Ubuntu Studio 11.04

:)

---

### Post by Cobra_MX5 on 2012-01-27
Had the same problem, solution worked for me as well on 11.04 AMD64 :) Thanks!!

---

