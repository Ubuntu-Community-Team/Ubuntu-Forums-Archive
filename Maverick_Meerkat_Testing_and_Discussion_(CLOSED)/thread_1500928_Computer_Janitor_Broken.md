---
title: "Computer Janitor Broken"
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mxboy15u on 2010-06-03
It does not appear to be scanning for stuff to remove anymore, anyone else experiencing that?

---

### Post by null_pointer_us on 2010-06-03
Yeah, I removed a bunch of stuff that it suggested, but I left some others installed (e.g. linux image and headers 2.6.32-22?).

Now it no longer suggests some of those for removal.

---

### Post by seeker5528 on 2010-06-03
> **mxboy15u said:**
> It does not appear to be scanning for stuff to remove anymore, anyone else experiencing that?

Seems to be working for me, it shows a list of packages it claims I no longer need and showed a left over blah-blah.dpkg.old file to delete.

Later, Seeker

---

### Post by cariboo on 2010-06-03
You guys are brave. :)

---

### Post by SoFl W on 2010-06-03
[FONT=Arial][SIZE=2]Number 4 "[/SIZE][/FONT][I][FONT=Arial][SIZE=2]Never use cleaning applications like Computer Janitor, even though that particular application comes by default in Ubuntu"

[/SIZE][/FONT][/I][FONT=Arial][SIZE=2][Seven fatal mistakes]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes") [/SIZE][/FONT]

---

### Post by TerminX on 2010-06-03
How about number 8: never trust silly lists that assume you're an idiot.

I especially love this gem:

> Even when you never use a particular default application: don't remove it. Reason: the default installation is an intertwined system that's dependent on shared supporting files, which makes the operating system run stable.

When you remove a default application, you run a risk of seriously damaging the system.
So now they're assuming the Ubuntu developers are idiots as well by implying they don't know how the dependencies field works when packaging software?

They might as well be warning people to never get out of bed on the off chance you might fall down and hit your head and die.

Anyway, if computer-janitor-gtk isn't showing you anything, try the "show previously ignored" option under the view menu.  It's probably just not finding anything new for you.

---

### Post by ranch hand on 2010-06-03
> **SoFl W said:**
> [FONT=Arial][SIZE=2]Number 4 "[/SIZE][/FONT][I][FONT=Arial][SIZE=2]Never use cleaning applications like Computer Janitor, even though that particular application comes by default in Ubuntu"

[/SIZE][/FONT][/I][FONT=Arial][SIZE=2][Seven fatal mistakes]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes") [/SIZE][/FONT]
Hey, thanks for the link.   I have a bookmark folder with stuff just for noobs.  This makes a great addition.

Most of the things they talk about there are just used by folks that have no desire to learn a thing about their system.  There are easier, safer way to do most of that built into Linux.

Ultamatix is just a stupid ego trip for the "developer".

---

### Post by seeker5528 on 2010-06-03
> **SoFl W said:**
> [FONT=Arial][SIZE=2]Number 4 "[/SIZE][/FONT][I][FONT=Arial][SIZE=2]Never use cleaning applications like Computer Janitor, even though that particular application comes by default in Ubuntu"

[/SIZE][/FONT][/I][FONT=Arial][SIZE=2][Seven fatal mistakes]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes") [/SIZE][/FONT]

Computer Janitor is a decent tool.

Sure you want to investigate before removing something and if there is doubt keep it, some paranoia is good. Saying you should never use it on the grounds that 'before you know it you damaged your system' seems overly paranoid.

Running it a second time though, apparently if you don't get rid of a package it will ignore that package in future runs and you have to choose to view previously ignored stuff. Maybe that is what the OP was seeing?

Later, Seeker

---

### Post by null_pointer_us on 2010-06-04
> **TerminX said:**
> Anyway, if computer-janitor-gtk isn't showing you anything, try the "show previously ignored" option under the view menu.  It's probably just not finding anything new for you.

Thanks, that was the solution.

I wondered why Computer Janitor kept demanding authentication when unticking one of those checkboxes. Apparently unticking the boxes added those packages to some ignore list.

That's bad software design IMO.

---

### Post by SoFl W on 2010-06-04
> **TerminX said:**
> How about number 8: never trust silly lists that assume you're an idiot.

Actually, I have violated about five of those rules.  I have used janitor but wondered if it was really a good idea.

---

