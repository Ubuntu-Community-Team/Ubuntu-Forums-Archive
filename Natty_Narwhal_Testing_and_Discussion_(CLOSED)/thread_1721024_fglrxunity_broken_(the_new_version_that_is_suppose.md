---
title: "fglrx/unity broken (the new version that is supposed to work!)"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Zorgoth on 2011-04-03
Using Natty beta 1 installed from a cd downloaded today, fglrx version 2:8.840-0ubuntu1 (which I believe is the version that is supposed to work) does not work with unity on my laptop (ATI Mobility Radeon HD 5470).  I get images like the attachment on logging in and it doesn't really improve.  Various areas of black and desktop background change as I attempt to do things.  Unity's panel/dock are running but are always pure black like in the screenshot.  When I open a program (using Alt-F2) compiz finally gives up and crashes.

fglrx works fine with compiz on Ubuntu Classic.

Anyone know what to do?

---

### Post by cariboo on 2011-04-04
DId you follow the instructions I linked to [here]("http://ubuntuforums.org/showpost.php?p=10618166&postcount=1")?

---

### Post by Zorgoth on 2011-04-04
I did see that page and I believe I did follow those instructions.  There is a slight ambiguity in them as there are two fgrx options on the second command (manual and automatic) - it looked like automatic was already selected so I tried manual.  Later I tried automatic as well.  Neither worked.

---

### Post by cariboo on 2011-04-04
Did you click on the ppa link at the bottom of the page, and install the daily version of Unity?

---

### Post by Zorgoth on 2011-04-04
OK that did it - I thought that because I had a newer version of unity than was in that repository I didn't need it but it was compiz.

---

### Post by Amaranth on 2011-04-04
Yeah, compiz has to do some tricks to get fglrx to allow it to use FBOs (which unity uses) so you need a compiz patch as well as the new fglrx.

---

