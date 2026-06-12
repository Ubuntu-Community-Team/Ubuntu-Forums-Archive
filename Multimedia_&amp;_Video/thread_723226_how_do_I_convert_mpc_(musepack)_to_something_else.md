---
title: "how do I convert mpc (musepack) to something else?"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by oskar2000 on 2008-03-13
I can play it, but I can't convert it.

soundkonverter can't open it
soundconverter crashes while trying to convert it
the nautilus audio conversion script is missing dependencies.


Has anybody successfully converted musepack?

---

### Post by frodon on 2008-03-13
Just install the musepack decoder and encoder on your system (if i remember well you just have to copy the 2 files in /usr/bin) and the nautilus script will be able to use them.
[http://www.musepack.net/index.php?pg=lin](http://www.musepack.net/index.php?pg=lin)

It worked for me when i did this.

---

### Post by oskar2000 on 2008-03-14
It's just a single binary with no dependencies? Why the hell isn't this in the repositories?!

---

### Post by frodon on 2008-03-14
I guess because mpc is fully proprietary and therefore should not be encouraged. And yes from what i remember they are binaries you can directly copy in /usr/bin where the nautilus script will look for them to enable mpc support.
If you have still issues tell me, i did that once so i'm sure it should work for you too.

---

### Post by oskar2000 on 2008-03-14
Yes, correct... that's the one that the nautilus script was missing.

And, yes... standard procedure worked as expected. If anyone else has this problem, just get the binary, make it executable (chmod +x) and copy it to /usr/bin to use it without having to type the absolute path.

---

