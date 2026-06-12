---
title: "Added a second tuner - 1 video source or 2?"
date: 2009-12-14
forum: Mythbuntu
---

### Post by Crusty Juggler on 2009-12-14
Just like the title says, I've added a second tuner.  I'm not sure if I should have a separate video source for each one for over the air broadcasts or if they should be fine sharing one.  Thanks!

---

### Post by My Name on 2009-12-14
I have two freeview DVB cards sharing one video source called "freeview".
It means I only need to do one channel scan.

---

### Post by ian dobson on 2009-12-14
Hi,

If both tuners can tune to the same channels, then add them both to the same video source. MythTV will then use whichever tuner is free.

Regards
Ian Dobson

---

### Post by NightStorm on 2009-12-14
> **Crusty Juggler said:**
> Just like the title says, I've added a second tuner.  I'm not sure if I should have a separate video source for each one for over the air broadcasts or if they should be fine sharing one.  Thanks!

Hey .. thanks for starting this thread, as I'm confused about this myself.  I've a related question that maybe someone could give me some advice on ..

I've both an HDHomerun and an HVR-2250.  The HDHomerun points to the antenna while the HVR-2250 to the Comcast cable (thus there are two tuners on each source).  I've currently set this up with two video sources each using my SchedulesDirect account.  One video source is called "OTA" which has the broadcast listings and the other is called "Comcast" which has the Comcast Digital listings.  The tuners are then associated with their respective video source.

I guess my first questions is:  Is this the correct setup for this kind of configuration?


My second question is: Is there anyway to avoid having multiple channels listed in the guide?  What happens now is that the OTA channels also come in via Comcast.  It would be nice if I did not have these common channels repeated for each instance (OTA and Comcast).  Ideally I'd like to have just the one channel and when I watch live TV or record I'd like MythTV to just select whatever tuner is free for that channel. (Btw: for some of the channels the duplicate entry will show "NO DATA" in the guide, even though the XMLId and everything else looks correct).

I also notice that when going through the guide that the channels that are on another source have a different color and can't be accessed via the guide (but they can by up-down channel when watching the live source).  Is there some setting for that somewhere (I've not been able to find it)?

TIA,

   - Bruce

---

