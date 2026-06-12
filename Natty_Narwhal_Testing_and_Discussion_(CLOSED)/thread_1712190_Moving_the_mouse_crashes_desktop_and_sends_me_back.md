---
title: "Moving the mouse crashes desktop and sends me back to login screen (ATI 9600 Mobility"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by crjackson on 2011-03-22
Okay, I've been out of this testing cycle for the most part (I've been beta testing the surgical ward of the V.A. hospital since Oct. last year, so far they are making good progress :) )

Here's the beef,

I updated my sources and Natty boots on up, then as soon as I touch my mouse pad or move the pointer with a USB mouse, the screen smears from top to bottom (it looks like the jump to warp speed on star trek as the stars smear). Then it dumps me back to the login screen.

Any suggestions. I'd like to play too....  :P

---

### Post by dino99 on 2011-03-22
today we have had some packages rebuilt to follow the new multiarch rules. Steve Langasek have warn about some issues till all the new packages be in place.

So try to isolate the package(s) to blame: check logs and uninstall graphic effects or/and compiz/unity... (mostly related to eglibc)

---

### Post by crjackson on 2011-03-22
Okay, so I'll check that out.  I'm downloading the daily live now, and I'll see how it does. Thanks.

---

### Post by crjackson on 2011-03-22
I couldn't get it to work out with the installed version, so I installed from scratch from the daily live image. It's working okay now. The dock on the left is awkward to use however. I'll probably switch to classic mode.

---

