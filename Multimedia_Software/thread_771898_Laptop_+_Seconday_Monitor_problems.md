---
title: "Laptop + Seconday Monitor problems"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Nick Venture on 2008-04-28
I installed Ubuntu tonight and everything went well except that Ubuntu seems to like my secondary monitor too much.

I have a 15 inch laptop (resolution 1280 x 800) and a secondary 22 inch monitor attached to it (resolution 1680 x 1050).  Ubuntu is only making use of latter's real estate and cloning in on the former.

When I check out Screen Resolution under System > Preferences I can see that ubuntu does see both monitors and recognizes the difference between the two but is not doing anything about separating them (even when I specify that I do not want any cloning).

I'm not sure where to begin in figuring out this problem.

---

### Post by chewearn on 2008-04-28
What graphic chipset do you have?

---

### Post by Nick Venture on 2008-04-28
It's an Intel graphics chipset on a Dell E1505 from 2006.

---

### Post by chewearn on 2008-04-28
I'm not familiar with Intel GPU, but I know Google-Fu.

You could try using xrandr to configure it.  Not sure about success.  Some example:

List detected displays and resolutions:
```
xrandr
```Autoconfigure:
```
xrandr --auto
```More information:
```
man xrandr
```[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

.

---

### Post by machadoug on 2009-06-24
Dear Chewearn,

Sorry to resurrect this topic, but I followed these steps (Dynamically setup with xrandr) and could not make this work on 8.04.

It was working out of the box with 9.04, however I had to downgrade because it didn't get the correct screen resolution, I have a Intel graphic card.
I decided to downgrade after I read [this post]("http://ubuntuforums.org/showpost.php?p=7509291&postcount=3").

Do you have any idea what else I might have to do?

Regards

---

