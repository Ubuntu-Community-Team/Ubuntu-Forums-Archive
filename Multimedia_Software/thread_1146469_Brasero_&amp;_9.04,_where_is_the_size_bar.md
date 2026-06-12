---
title: "Brasero &amp; 9.04, where is the size bar?"
date: 2009-05-02
forum: Multimedia Software
---

### Post by UranUtan on 2009-05-02
Hi,

May be I did something wrong. Brasero now looks different. When filling files into the project, I used to see a progression bar in the lower right side to show the percentage of how full is the CD/DVD.

Now this bar is nolonger displayed. I've looked in all the options but couldn't find how to display this "Size bar".

Can you please suggest a solution?
Thanks in advance.

---

### Post by Yellow Pasque on 2009-05-02
They got rid of the size bar in Brasero 2.26 (an unpopular decision): [http://bugzilla.gnome.org/show_bug.cgi?id=554201](http://bugzilla.gnome.org/show_bug.cgi?id=554201)
You can try gnomebaker.
You could also try K3b (my personal favorite). If you do that, use this command to avoid installing extra KDE programs you don't need:
```
sudo apt-get --no-install-recommends install k3b libk3b3-extracodecs
```

---

