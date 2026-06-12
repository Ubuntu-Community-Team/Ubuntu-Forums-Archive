---
title: "Unity bugs out if I press &quot;See X more result(s)&quot;"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dacovale on 2011-04-11
Attached is a screenshot of my problem, followed by the before and after pic.

As soon as I press "See one more result" (or "See 80 more results" depending on how many are hidden) the menu is cleared. As I move the mouse pointer around, I "uncover" the icons I happen to hover over, as well as the option to hide the extra applications again. If I choose to hide them, status quo is restored, and I can see everything I should be able to.

Anyone else seeing this?

I'm on an AMD64-system which was upgraded to 11.04 from a fresh install of 10.10
I actually don't know what product or component to file the bug against, so if it's not known/filed, I'd also like to know where I report Unity-bugs :p

EDIT: Ok, so I think I found where to file the bugs, [https://bugs.launchpad.net/unity/+filebug]("https://bugs.launchpad.net/unity/+filebug") right?
Still can't find any bug that matches any of my search terms. But I must admit I'm not really sure how to define the bug in searchable terms.


EDIT2:
I've now installed 11.04 on another computer, this time a 32-bit. It doesn't have the same issue. So in a my sample of two, this is limited to the 64-bit version of Ubuntu.

---

### Post by dacovale on 2011-04-13
Posted bug-report: [https://bugs.launchpad.net/unity/+bug/759835](https://bugs.launchpad.net/unity/+bug/759835)

---

### Post by Grenage on 2011-04-13
That looks like it could be a graphics driver issue, what card/driver are you using?

---

### Post by dacovale on 2011-04-13
ATI Radeon X1550

driver:radeon

---

### Post by Grenage on 2011-04-13
You're not alone:

[https://bugs.launchpad.net/unity/+bug/726888](https://bugs.launchpad.net/unity/+bug/726888)
[https://bugs.launchpad.net/unity/+bug/666718](https://bugs.launchpad.net/unity/+bug/666718)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033)

---

### Post by dacovale on 2011-04-13
well, you're way better than me at searching, that's for sure :)

Should I list those three bugs in my report and let the bug-triage team decide which one it's a duplicate of, or ... ?

EDIT: After reading further, I'll add a note that it's a dup of #726033

thanks for the help :)

---

### Post by Grenage on 2011-04-13
No problem! :)

I actually just did a Google search for "RV516 Unity"; I tend to have more luck that way.

---

