---
title: "how to change unity 2d behaivor to always visible mode?"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Marcelo Ramone on 2011-04-08
Hello,

In Ubuntu 11.04 unity-2d is setup in auto-hide mode, my intention is to change this behaivor for ALWAYS VISIBLE mode. 

How to  do it?

Thank you.-

---

### Post by Mark Phelps on 2011-04-09
Ubuntu 11.04 is still under Development.  This forum is for versions that have been released.

Please post your 11.04 questions to the proper Natty Development forum.

thanks

---

### Post by Perfect Storm on 2011-04-09
Moved to testing forum.

---

### Post by rapiertg on 2011-04-09
Open gconf-editor and go to desktop > unity-2d > launcher and check use_strut and change hide_mode to 0.
Cheers

---

### Post by x-shaney-x on 2011-04-09
I came here to post the same question.
So thanks to rapiertg for clearing it up.

Of course it's such an obvious option I can't believe I didn't figure it out myself ;)

---

### Post by bcbc on 2011-04-09
This is another way: [http://askubuntu.com/questions/9865/will-the-unity-launcher-auto-hide/31418#31418](http://askubuntu.com/questions/9865/will-the-unity-launcher-auto-hide/31418#31418)

Personally I think this should be installed by default - I guess it will by release time

---

### Post by x-shaney-x on 2011-04-09
> **bcbc said:**
> This is another way: [http://askubuntu.com/questions/9865/will-the-unity-launcher-auto-hide/31418#31418](http://askubuntu.com/questions/9865/will-the-unity-launcher-auto-hide/31418#31418)

Personally I think this should be installed by default - I guess it will by release time

Unity 2D is metacity based, it's "standard" Unity which uses compiz so that won't help.

---

### Post by bcbc on 2011-04-09
> **x-shaney-x said:**
> Unity 2D is metacity based, it's "standard" Unity which uses compiz so that won't help.
Ah... I missed that ;)

---

