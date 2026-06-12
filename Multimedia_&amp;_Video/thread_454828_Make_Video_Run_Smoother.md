---
title: "Make Video Run Smoother?"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by computergee on 2007-05-25
I'm a big movie watcher, and I do most of my watching on the computer. Sometimes I like to browse the web while watching a movie, on the same machine. This is where my problem arises. It seems every time I click a link  or do something that makes the browser load (Firefox), the video starts stuttering. The audio continues playing fine, and when the load is over it is all smooth again. It also smooths out if I click on the video player (Kaffeine) to give it focus. Does anyone know of a way to give the video player higher priority or something so that it plays the movie smoothly all the way through?

Here are my system specs:

Kubuntu
AMD Athlon 64 3000+
2gb DDR RAM
AGP 7600gs

Thanks in advance.

---

### Post by Cappy on 2007-05-26
I think the command is "nice"

Maybe if you start Kaffeine with this:
```
nice -n 9 kaffeine
```

I can't tell you exactly how to use nice. I'm not sure if the "9" is added on to the default value of "10" priority or if it sets it to "9" priority. The man page isn't clear on this. I've noticed setting a priority adjustment of "-1" or less requires sudo. -20 is the most priority, 20 is the least priority.

If that line only decreases priority, you could start firefox with it instead.

---

