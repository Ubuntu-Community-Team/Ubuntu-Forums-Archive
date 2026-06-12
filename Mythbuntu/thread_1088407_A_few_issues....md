---
title: "A few issues..."
date: 2009-03-06
forum: Mythbuntu
---

### Post by mathog on 2009-03-06
I'm using the VDPAU version now, with the 8.29 driver.  There are a few
issues, are they specific to this version, all versions, my machine...

1.  While watching TV with the sticky keys off.  At first the right/left arrows work as described, left jumps back 5 seconds, right
jumps forward 30.  Then after a bit, poof, they do nothing.  Hit "escape", wait a bit, start watching again and it works - for a while.

2.  With the sticky keys on, right arrow toggles fast forward up, left arrow toggles reverse up.  So far so good.  Eventually it gets up to 180X, then it rolls back to 3X, there seems to be no way to avoid that.  Worse, in fast forward when it hits the end of a live recording (that is a show which is being watched while it is being recorded) it jumps from the end (current time) back to the beginning.  It really should drop into "play" at this point instead.  For rewind it does the right thing and drops into "play" when it hits time 0.

3.  With the sticky keys on, press right arrow.  As described in the documentation, space exits to play, 4-9 set the speed to 30,60,120,180X.  That part is as described.  0 is supposed to play at normal speed with the time indicator on the screen - it is ignored.
1 and 2 are supposed to be slower than normal FF/RW, 3 is supposed to be normal (3X).  In fact 1->3 are 5X 10X and 20X respectively.  This "feels" like a design change in the program that is not yet represented in the documentation. Is there currently a method to play slower than 1X?

4.  When paused.  Left arrow is to rewind one frame.  It does, but to rewind ANOTHER frame one must first wait about 2 seconds before pressing the key again.  Right arrow does the same thing in the other direction.  The ">" and "<" keys advance/rewind in 1 second increments, as documented, without needing the delay.

5.  There seems to be no commercial flagging taking place, at least when a program is recorded by pressing "R" while watching it.  Under mythtv-setup "start auto-commercial flagging jobs when the recording starts" is checked, commercial flagger command is "mythcommflag".  However, in the resulting recording, now 30 minutes after it terminated, the relevant commands do nothing. For instance, when a commercial starts hitting "Z" has no effect.  Similarly, going into the EDIT mode and then pressing "Z" also has no effect.  The mythbackend log file doesn't show commercial flagging ever starting.  However, for shows which are recorded by programming them ahead of time, commercial flagging does start and works properly.

That's enough for now.

---

### Post by newlinux on 2009-03-06
I don't use sticky keys or VDPAU and don't have any of those problems. In fact I never use FF and rewind (only skips and direct seeking, I'm impatient). but...

3. You can use the timestretch feature to play slower than 1X speed. I forgot the default key binding but you can get to it in the onscreen menu.


5. Whenever I record an an in progress show as you've described, I have to explicetily run a commflag job (you can do this from the Watch Recordings screen). I guess this is just the way it is.

---

