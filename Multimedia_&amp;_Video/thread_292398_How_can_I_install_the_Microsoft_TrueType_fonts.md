---
title: "How can I install the Microsoft TrueType fonts?"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by bobsta63 on 2006-11-03
Hi all,

Anyone know how to install Micro$oft TrueType fonts?

Can this be done using **apt-get**? Whats the command?

Thanks in advance,

Bobby

---

### Post by NetworkGuy on 2006-11-03
Install Automatix2

[www.getautomatix.com](www.getautomatix.com)

Then choose msfonts from within there.   Easiest way I found to get them installed.

---

### Post by Jorge on 2006-11-03
After installing the MS TTF fonts from Microsoft (using Automatix), make or locate the .fonts directory inside your home directory and drop there all the .ttf fonts you need, copied from a Windows machine/partition.

Enjoy!

---

### Post by eg-maverick on 2006-11-30
> **NetworkGuy said:**
> Install Automatix2

[www.getautomatix.com](www.getautomatix.com)

Then choose msfonts from within there.   Easiest way I found to get them installed.

I have edgy (6.10) and Automatix2. I can't find anything that talks about msfonts in the menus when I run Automatix2. Can you provide more detail?
Thanks.
Craig

---

### Post by djlosch on 2006-11-30
```
sudo apt-get install **msttcorefonts**
```

the problem with this package is that it runs a wget script and installs different subarchives.  sometimes certain fonts will not resolve from their mirrors, and you'll have to start it over again.

edit: i don't know offhand what repo it's in.  i just use the max repos on ubuntuguide.

---

