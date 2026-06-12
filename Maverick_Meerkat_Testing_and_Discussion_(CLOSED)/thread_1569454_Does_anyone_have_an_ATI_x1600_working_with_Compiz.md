---
title: "Does anyone have an ATI x1600 working with Compiz?"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jim March on 2010-09-06
I actually have a variant of the X1700 (FireGL V5250 in an IBM T60p) but I understand the issues are similar and the X1700 is more common.

Right now with either the standard Maverick setup or the xorg-edgers PPA I have a good, quick display but no Compiz.  GLXGears works, I'm at 1680x1050, etc, so I do have the open-source radeonhd drivers working.  So...I'm not complaining TOO hard but I'd like the cube :).

Now, I haven't done a clean install yet.  I had Lucid running on my old Dell laptop with an Intel 965 craptastic video card.  I'd already upgraded the Dell hard disk to a 250gig so I pulled that drive out and dropped it right into the IBM.  No problem.  But, I suspect I may have some old setting laying around blocking Compiz, because in Lucid I didn't have Compiz on the Dell either.

So, if somebody DOES have a card like my new ATI working with Compiz in Maverick, I guess it's time to go do a totally clean rebuild, OR figure out what the setting might be...

Thanks!

---

### Post by Jim March on 2010-09-06
Got it - turned out to be the same issue as:

[http://forum.eeebuntu.org/viewtopic.php?f=41&t=2682](http://forum.eeebuntu.org/viewtopic.php?f=41&t=2682)

Just had to go into Synaptic and look for key pieces of Compiz that were somehow left out.  Compiz-gnome for starters, it pulls the other two it needs off of that.

I solved it by doing "compiz --replace" at a terminal and googling on the resulting errors.

Got the cube back - kewl!  I have a key demonstration for court either end of this week or early next, I want Compiz for the visual kick.  I'm doing a demo on the potential security risks to elections from funky wireless networking...long story.

---

