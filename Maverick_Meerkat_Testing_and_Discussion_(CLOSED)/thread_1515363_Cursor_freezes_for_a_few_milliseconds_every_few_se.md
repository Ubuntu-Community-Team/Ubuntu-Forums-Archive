---
title: "Cursor freezes for a few milliseconds every few seconds (lol)"
date: 2010-06-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-06-22
Hello,

I'm having an issue with my cursor, when I move it around, every few seconds I can't move it for a few milliseconds (I can't explain that good). I think this started happening after the x.org 1.8 updates and I've had this issue for a few weeks and is starting to frustrate me.

I have an Intel Dual Core processor, 4Gb RAM and the x64 bit fully updated Maverick.

Lee

---

### Post by philinux on 2010-06-22
> **lee.jarratt said:**
> Hello,

I'm having an issue with my cursor, when I move it around, every few seconds I can't move it for a few milliseconds (I can't explain that good). I think this started happening after the x.org 1.8 updates and I've had this issue for a few weeks and is starting to frustrate me.

I have an Intel Dual Core processor, 4Gb RAM and the x64 bit fully updated Maverick.

Lee

Try doing an update there's a new kernel today. 2.6.35.5.5

---

### Post by go7Ul1ai on 2010-06-22
Thank you for the reply, unfortunately it hasn't solved the problem. Is anyone else having this problem?

I am using an Advent Roma 3000 (uncommon I know)

---

### Post by siriusguy on 2010-06-22
I was having the same problem.   I removed package "unclutter" which is supposed to hide the cursor when the screen is inactive and it seems to have helped.

I'm not 100% sure it's a fix but you might see if you have unclutter installed.

----- later ----

Nope, that didn't fix it.   Still having issues with this.

---

### Post by jppr on 2010-06-23
This  morning I did a clean installation and that the same issue is still.

Edit. Sorry, my bad... cursor don´t freeze, it´s gone after few seconds. when i move mouse cursor is back but gone again 
after few seconds = )

---

### Post by Slug71 on 2010-06-23
I get this after boot/log-in for about a minute, sometimes longer.

---

### Post by VMC on 2010-06-23
Strange but my mouse pointer after a second or two disappears and reappears if I move my mouse, but it doesn't freeze up. 

This happened for the first time after todays, June23rd, install.

---

### Post by pferraro on 2010-06-23
Does everyone experiencing this problem have a multi-core box?  If so, might this have something to do with irqbalance?
There's a new release in the build queue containing this in its changelog:
* New upstream release, this release offers better support for 2.3.35.
(Hence my suspicion...)

---

### Post by ranch hand on 2010-06-23
I am on a multi-core box (see sig) and have not seen this problem yet at all.

---

### Post by pferraro on 2010-06-23
> **ranch hand said:**
> I am on a multi-core box (see sig) and have not seen this problem yet at all.

Do you have irqbalance installed?  I believe it was added as a "recommends" dependency to ubuntu-standard in lucid.
It's a good idea for multi-core chips, since it effectively allows interrupt load balancing across your cores - and should result in a more responsive system.  I dunno if it is still wise on the new i3/5/7 mobile chips, since it might adversely affect battery life as it might cause unnecessary core wakeups.  Come to think of it, perhaps that's a possible cause of the freezing?

<addendum>The new irqbalance version has been uploaded.  See if you still have the problem after upgrading.</addendum>

---

### Post by ranch hand on 2010-06-23
> **pferraro said:**
> Do you have irqbalance installed?  I believe it was added as a "recommends" dependency to ubuntu-standard in lucid.
It's a good idea for multi-core chips, since it effectively allows interrupt load balancing across your cores - and should result in a more responsive system.  I dunno if it is still wise on the new i3/5/7 mobile chips, since it might adversely affect battery life as it might cause unnecessary core wakeups.  Come to think of it, perhaps that's a possible cause of the freezing?

<addendum>The new irqbalance version has been uploaded.  See if you still have the problem after upgrading.</addendum>
Never heard of it.  Went to synaptic and checked.  It is not installed.

I also do not worry too much about load balancing.  My cores run, all the time, at 99-100% due to the way I have my boinc settings.  This will test your pre-release OS to the max.

I very rarely see any performance problems.  It is set to cut back if I really need the cpu power.  I have system monitor added from the add to panel menu and right now, as always, it is solid blue.

The only time I baby it is at boot up.  I do wait for bootchart to finish before I start boinc.

---

