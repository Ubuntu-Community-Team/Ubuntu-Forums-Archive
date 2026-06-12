---
title: "Amarok issue"
date: 2008-11-26
forum: Multimedia Software
---

### Post by ndruu on 2008-11-26
So every time I start amarok, it runs the "first time wizard". Even though I input the settings i want, it doesn't remember them. I can't get it to recognize my library either, I'll go to configure amarok and I'll set the location for my music library, apply/ok, and then it'll immediately forget what I just set. 

Whats going on?

I'm running a fairly recent install of Ubuntu 8.10, but I prefer Amarok as a media player so that was one of the first things I installed. If more information about my system would help, feel free to ask.

Thanks for any help in advance.

---

### Post by Zaraphrax on 2008-11-26
Try this:

```
sudo apt-get remove amarok
```

Then:

```
sudo apt-get install amarok
```

---

### Post by tjko on 2008-11-26
I don't know how fresh of installation your Ubuntu 8.10 is, but in any case, I agree with Zaraphrax, you should try to simply reinstall amarok.

Let us know if that doesn't fix it.

---

