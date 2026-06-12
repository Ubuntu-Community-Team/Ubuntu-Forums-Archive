---
title: "Problem with Spotify under Wine. Ubuntu 9.10"
date: 2009-11-16
forum: Multimedia Software
---

### Post by peteho1990 on 2009-11-16
Since upgrading to the new version of Ubuntu 9.10. Spotify has trouble playing sound. It will play, but the music is jumpy and there's an odd fuzzy sound added!
Any idea's how to fix it?
Cheers

---

### Post by kostkon on 2009-11-16
Try removing the *wine* package and install the *wine1.2* one.

Or even better, you could get the latest by adding Wine's PPA to your software sources list. Just go to *System &#8594; Administration &#8594; Software Sources* in the *Third Party Software* tab, press *Add* and give
```
ppa:ubuntu-wine/ppa
```
and then install the *wine1.2* package.

---

### Post by ukblacknight on 2009-11-16
Unrelated to the original post, but does anyone else find that when you launch spotify, it starts off at a normal size, and as soon as you click on anything in the window, it resizes itself to quite a small window?

---

### Post by peteho1990 on 2009-11-16
Cheers. It works brilliantly now :D

---

### Post by .nedberg on 2010-02-23
> **ukblacknight said:**
> Unrelated to the original post, but does anyone else find that when you launch spotify, it starts off at a normal size, and as soon as you click on anything in the window, it resizes itself to quite a small window?

Old thread, but yes, I see that every time I launch Spotify. Did you fix it?

---

### Post by andygait on 2010-02-27
> **kostkon said:**
> Try removing the *wine* package and install the *wine1.2* one.

Or even better, you could get the latest by adding Wine's PPA to your software sources list. Just go to *System &#8594; Administration &#8594; Software Sources* in the *Third Party Software* tab, press *Add* and give
```
ppa:ubuntu-wine/ppa
```and then install the *wine1.2* package.


Huge thanks for this.

Spotify has been driving me nuts for the last week or so... all sorted now. :D

You're a star.

---

### Post by Aerodynamic on 2010-03-07
Works for me also :) Have already installed wine from the official respos..removed them, added the repos from wine HQ and problem solved.

---

