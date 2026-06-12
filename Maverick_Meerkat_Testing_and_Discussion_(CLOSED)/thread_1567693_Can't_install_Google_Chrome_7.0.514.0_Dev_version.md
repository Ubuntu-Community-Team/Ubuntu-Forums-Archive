---
title: "Can't install Google Chrome 7.0.514.0 Dev version"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-09-04
I have just noticed that a new dev version of google chrome have been releasd so i downloaded the latest google-chrome-unstable_current_i386.deb 
deb file but it does not install i start the file it start installing but in the end it doesn't change to reinstall and it doesn't update the current 
version(and i am installing when the google chrome browser is close of course)

What can i do about it?

Thanks in advance.

---

### Post by MacUntu on 2010-09-04
Are you using Gdebi? For whatever reason it fails to install packages, but using the command line works fine. Just run
```
sudo dpkg -i <path-to-deb-file>
```

---

### Post by aviramof on 2010-09-04
Thanks for the information i would give it a try and i hope the problem with Gdebi would be fix soon because it sound like a pretty serious problem for me.:)

---

### Post by go7Ul1ai on 2010-09-04
> **aviramof said:**
> Thanks for the information i would give it a try and i hope the problem with Gdebi would be fix soon because it sound like a pretty serious problem for me.:)

Try right-clicking the .deb file and select "open in Ubuntu Software Centre" (or something along the lines), debs should open in software centre now..

Or you could just add the Chromium Daily PPA?

---

