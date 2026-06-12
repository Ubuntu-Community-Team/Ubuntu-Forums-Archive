---
title: "running sudo lshw seems to be a bit of an issue"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-09-01
In the past lshw or lshw <whatever> was usually advised to be run w/ sudo
That doesn't appear to be something you'd want to try atm on maverick

Was trying sudo lshw -html > hardware.html for some other thread, 1 attempt produced an odd error message, 2nd or 3rd will crash the terminal and or X

lshw seems to work fine atm

---

### Post by utnubuuser on 2010-09-01
I'd be inclined to try piping through cat instead of direct to .html> sudo lshw -html | cat > lshw.html

---

### Post by VMC on 2010-09-01
Your right. In fact all I needed to do was type ```
sudo lshw
``` twice before a had a kernel crash. app crash dialog came up and I was able to complete it and filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627848") using firefox, but couldn't give any more info because everything was frozen. Surprisingly Firefox worked.

---

### Post by mc4man on 2010-09-01
Yeah it's the sudo that's the issue - plain lshw works without error or crash
(lshw or lshw <whatever>

The results of any of the lshw commands  work ok though you don't always get full info without sudo (Ex. lshw -C disk

---

### Post by glepore70 on 2010-09-01
Already reported at:
[https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/620114](https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/620114)
and
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/623140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/623140)

---

### Post by seeker5528 on 2010-09-01
Bug #620114 seems most like what happens to me, so I did the "me too" thing, clicked on the "This bug affects X people. Does this bug affect you?" link.

Later, Seeker

---

### Post by cariboo on 2010-09-01
I'm also plagued by #[lpbug]620114[/lpbug], I added my affects me too.

---

