---
title: "Picasa complains about nvidia access rights"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by pschalkx on 2007-02-13
Hi !

I installed Picasa on Ubuntu 6.10 and get the following message when firing it up from any other user than the main user (the one that can run sudo):

[I]/dev/nvidia0 or /dev/nvidiactl are not accessable.  Picasa will crash if these files are not accessable. To fix this, as root, please run:

chmod 666 /dev/nvidia0 /dev/nvidiactl[/I]

As a workaround, I go sudo and do the chmod to 666 of the two files, and picasa runs until machine is rebooted.

Any fixes available?

(AMD 64 running regular Ubuntu 6.10, Nvidia GeForce 6150).

Rgds,

Philip

---

### Post by dimbulb1024 on 2007-02-16
I'm having the same problem on a Dell Inspiron 6000 with 1.7GHz Intel Pentium M and Intel 915GM graphic chipset.

Throwing me for a loop.

---

### Post by phetre on 2007-05-21
Hi PSChalkx and DimBulb1024. I had the same problem with the secondary user on my Feisty laptop, which also uses an Intel chipset. In my case the solution was simple: [http://ubuntuforums.org/showthread.php?p=2695663#post2695663](http://ubuntuforums.org/showthread.php?p=2695663#post2695663)
If you haven't already solved it, I hope this helps!

---

