---
title: "DeVeDe Problems"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by tblehr on 2007-04-23
I'm using DeVeDe 2.9 to convert my AVI to DVD.

Some videos come out perfect, while most convert with lines going through the movie.

The audio is fine and the original video doesn't have the lines.

I was thinking about upgrading from 2.9 to the newest 2.13, but I don't know how to install tarballs, I always just stick with the repositories and 2.9 is the newest in the repositories.

If anyone could help me out or point me to another thread, that would be awesome.  Especially a good thread about installing tarballs, I really want to learn how to install them.

Thanks!

-Terrence-

**[COLOR="Red"]Got on the IRC channel, deinterlacing issue....fixed![/COLOR]**

---

### Post by reclusivemonkey on 2007-04-23
> **tblehr said:**
> 

**[COLOR="Red"]Got on the IRC channel, deinterlacing issue....fixed![/COLOR]**

Why don't you share the solution here for anyone else searching on this problem?

---

### Post by taurus on 2007-04-23
```
cd ~/Desktop
tar xvjf devede-2.13.tar.bz2
cd devede-2.13
sudo ./install.sh
```

---

### Post by tblehr on 2007-04-24
> **reclusivemonkey said:**
> Why don't you share the solution here for anyone else searching on this problem?

It was a deinterlacing issue.  I had deinterlacing off and just needed to switch it on in the settings, works great now!

Thanks taurus for that info, appreciate it!

---

