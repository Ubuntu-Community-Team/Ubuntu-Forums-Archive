---
title: "[SOLVED] mythtv is already using all available inputs"
date: 2007-11-23
forum: Mythbuntu
---

### Post by spinlock99 on 2007-11-23
Hey all,

I just installed Mythbuntu and my hardware seems to be working OK (hauppauge wintv 878/9 in a Cisnet box).  I can watch TV using xawtv but not in MythTV.  When I fire up MythTV I get the following error:

[INDENT]mythtv is already using all available inputs for the channel you selected, if you want to watch an in-progress recording select one from the playback menu. If you want to watch livetv cancel one of the in-progress recordings from the delete menu. 
[/INDENT]

I'll post up some screen shots of my MythTV config when I get home.

---

### Post by AusIV4 on 2007-11-23
In MythTV setup, have you setup tuners and associated them with show lineups? If not, MythTV isn't aware of any TV tuners.

---

### Post by spinlock99 on 2007-11-25
OK, progress.  I'm not getting that error anymore but I do get a blank screen now.  Here's my configuration:
General --

---

### Post by spinlock99 on 2007-11-25
General (cont...) --

---

### Post by spinlock99 on 2007-11-25
Capture Card Setup -- Hauppauge Win-TV 878/9 tuner card

---

### Post by spinlock99 on 2007-11-25
Video Source Setup --

---

### Post by spinlock99 on 2007-11-25
Input Setup --

---

### Post by spinlock99 on 2007-11-25
And, Chanel Editor Setup --

---

### Post by spinlock99 on 2007-11-27
I figured it out.  It was the Capture Card that was wrond.  I have to use the V4L drivers with my card and not the MPEG2 (even though the manual says to use the MPEG2 which is where I went wrong.  The set-up right out of the box was the right one),

And, of course, the screen shots:

---

### Post by superm1 on 2007-11-28
Glad you solved this (sorry you uploaded all those screenshots before someone identified the issue though).

The manual states that if you have a Hauppauge PVR-XXX series card to use MPEG2, but you only have a normal Hauppauge card so that is why you us V4L.

---

### Post by spinlock99 on 2007-11-28
> **superm1 said:**
> Glad you solved this (sorry you uploaded all those screenshots before someone identified the issue though).


It is kind of a pain to take screen shots of everything but that's the best way I've found to document gui applications.  To me, screenshots are the equivilant of cutting and pasting commands from the prompt when you ask for help on a mail list.  And, now I have a nice document for the next time I install Mythbuntu and, hopefully, someone else might find them usful too.

Thanks,
Andy

P.S. Is there any problem with posting up this many screenshots?  I think it's helpful but if it uses up too much bandwidth I can tone it down.

---

### Post by superm1 on 2007-11-28
> **spinlock99 said:**
> 
P.S. Is there any problem with posting up this many screenshots?  I think it's helpful but if it uses up too much bandwidth I can tone it down.
There shouldn't be any issues with it.  I know personally I like it better because then you can see "every" setting someone had that they might end up "overlooking" when trying to help them.

---

