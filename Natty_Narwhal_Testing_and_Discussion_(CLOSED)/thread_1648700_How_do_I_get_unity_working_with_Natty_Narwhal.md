---
title: "How do I get unity working with Natty Narwhal?"
date: 2010-12-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sashin on 2010-12-19
I know its not my graphics card, I can set compiz to extra and Unity worked fine with Maverick. But for some reason all I get is the gnome desktop under Natty, also firefox is version 3.6 something, not 4. But its definitely Natty Narwhal, when I go to system-->about ubuntu.

---

### Post by Harry33 on 2010-12-19
> **Sashin said:**
> I know its not my graphics card, I can set compiz to extra and Unity worked fine with Maverick. But for some reason all I get is the gnome desktop under Natty, also firefox is version 3.6 something, not 4. But its definitely Natty Narwhal, when I go to system-->about ubuntu.

Well we can see that if you post here the content of the following file in your system:
/etc/apt/sources.list

You should not find the word maverick in that file.
Sources.list determines all your updates.

---

### Post by Sashin on 2010-12-19
Maverick is everywhere! There is no natty? could you please paste yours here so I can copy it?

---

### Post by Harry33 on 2010-12-19
> **Sashin said:**
> Maverick is everywhere! There is no natty? could you please paste yours here so I can copy it?

No do not copy any others sources.list into your system.
That can cause breakage.

We can only help you if you post here yours.
You see, systematically by replacing the word maverick with the word natty may also break your system.
It depends so much on what additional PPA's you are using.
Also bear in mind that Natty has already gone through several different API/ABI upgrades. Upgrading may not be so easy. This is still only alfa1 we are talking about here. It is very far from stable yet.

---

### Post by Sashin on 2010-12-19
Just installed, no additional PPAs.

---

### Post by Sashin on 2010-12-19
Okay figured this out! Turns out with Brasero on the other computer I accidently clicked on the maverick image, coincidentally there was a glitch that  made maverick read 11.04 which tricked me into actually believing I had installed 11.04 when it was actually 10.10

All I have to do is burn the right image and reinstall!:popcorn:

---

