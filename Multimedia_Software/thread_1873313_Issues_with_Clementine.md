---
title: "Issues with Clementine"
date: 2011-11-01
forum: Multimedia Software
---

### Post by haggus71 on 2011-11-01
I tried out Clementine, and it works great streaming radio...for about a half hour.  That's when the Unity UI craps itself and freezes, leading to the necessity of a hard kill and reboot.  This happens whether I use 2D or 3D.  Using Streamtuner with Audacity has no such issues, as I've been able to use that for hours with no problems.

Is this due to the Unity interface?  Or is it some bug in Clementine, due to it being based on KDE software(Amarok)?

On an HP w/ dual core AMD vision processor, 4g RAM, AMD M880G/HD4250 graphics w/256m RAM.

---

### Post by SeijiSensei on 2011-11-01
This doesn't happen when running Clementine on KDE.  I stream a radio station regularly with Clementine, and it will run continuously for hours unless I stop it.

---

### Post by haggus71 on 2011-11-01
I guess I might have to add some kde support files, or just stick to this.  Though it stinks not having Shoutcast on the new streamtuner.

---

### Post by liquidmonkey on 2011-11-02
have been having clementine issues since i installed it last week.
plays great for 30 or 40 minutes, then if i access a menu, the entire unity desktop comes to a halt for between 5-15 minutes, depending how many menus i try to open.

really sucks since its such a good player!

---

### Post by liquidmonkey on 2011-11-03
can now confirm that it is indeed clementine causing a freeze.
using terminal and 'top', its clear that the 'unity-panel-ser' is using 96-100% of the cpu whenever clementine is on.

as soon i force quite clementine, it all goes back to normal.

any ideas?

---

### Post by haggus71 on 2011-11-03
I'm thinking something to do with it using a lot of the same resources as Unity? Maybe it's linked to its kde dependencies, being a re-engineering of Amarok 1.X.

---

### Post by liquidmonkey on 2011-11-03
not sure but it would be great if clementine OR the unity people would release a bug fix :)

---

### Post by Stovey on 2011-11-03
Hi, I had the same issue this morning, just "test-driving" Clementine for the first time.  And then everything sort of froze, but "ghost-windows" or outlines sort of showed up when clicking on icons and whatnot.  But Clementine kept on playing lol.  I had to pull battery and shutdown.

I am using Ubuntu 11.10 on a netbook: Acer Aspire 1810T.

I wish I could find an internet radio station that plays AC/DC, Guns & Roses, etc...

---

### Post by liquidmonkey on 2011-11-07
> **Stovey said:**
> Hi, I had the same issue this morning, just "test-driving" Clementine for the first time.  And then everything sort of froze, but "ghost-windows" or outlines sort of showed up when clicking on icons and whatnot.  But Clementine kept on playing lol.  I had to pull battery and shutdown.



next time it freezes, wait 5 minutes until it unfreezes then go into terminal, type 'top'.
that gives u a task manager like interface.
now ctrl-c out of it.
and 'killall clementine'

now your desktop is back.

---

### Post by liquidmonkey on 2011-11-07
have been running clementine today for 4 hours and all menus are working fine!
no ghost menu or freezing, maybe it was fixed in a recent update?

any1 else?

---

### Post by haggus71 on 2011-11-10
I've been running it since last night, and have no issues; but I'm using the Gnome shell instead of Unity.  I just like the look better, now.

---

