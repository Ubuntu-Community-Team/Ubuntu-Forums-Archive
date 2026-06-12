---
title: "Quick question about sources.list...mythtv"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by Rictus on 2007-04-22
In the instructions to set up a server for MythTv it says to make the sources.list have this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

Mine has all those, but like this:

deb [http://us.archive.ubuntu.com/ubuntu/fiesty](http://us.archive.ubuntu.com/ubuntu/fiesty) main
deb-src [http://us.archive.ubuntu.com/ubuntu/fiesty](http://us.archive.ubuntu.com/ubuntu/fiesty) main

So can I just go through and delete the "us" part? Or do I need both the old ones and the new ones?
Also do I need to modify the deb-src lines if I modify the deb lines?

Thanks
Rick

---

### Post by Titus A Duxass on 2007-04-22
You can delete the US part, but it is not necessary.
Mine have DE in them and they appear to work.

The US is just so that you use a "local" mirror.

I would hash out the src lines,

---

### Post by Rictus on 2007-04-22
Ok, just trying to avoid any possible errors this time through.
Much thanks.

---

