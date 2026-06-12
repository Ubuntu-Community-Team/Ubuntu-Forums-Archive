---
title: "Displaying image full screen from bash"
date: 2011-12-02
forum: Multimedia Software
---

### Post by funkytwig on 2011-12-02
Hi,

I have done a bit of googling and cant work out how to display and image full screen for a predetermined amount of time then exit back to script.  I have found ways of displaying image full screen from a script but not getting the image viewing program to exit after a predetermined amount of time (i.e. .2 of a second).

Any ideas?
Ben

---

### Post by Lars Noodén on 2011-12-02
Something like this?

```

gwenview *image.png* &
sleep 2
kill $!

```

I'm not sure how to get fractions of a second.  Maybe some other program can do that granularity.

---

