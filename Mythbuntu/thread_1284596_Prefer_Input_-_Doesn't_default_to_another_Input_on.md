---
title: "Prefer Input - Doesn't default to another Input on Conflict"
date: 2009-10-06
forum: Mythbuntu
---

### Post by bsntech on 2009-10-06
Hello all,

I am working with Ubuntu Karmic 9.10 currently.  This same problem plagued me in 9.04, however.

Quick background, I have two tuners installed:

PVR-150 (Analog Tuner)
HVR-1600 (Has both an Analog and Digital Tuner)

I have two channel Inputs - one is called "Analog" and the other is "Digital" for the TV lineups.  Both the PVR-150 and the analog side of the HVR-1600 use the "Analog" input while the digital side of the HVR-1600 uses the "Digital" side of the input.

Now, for the problem.  I use the digital card to record as much TV as possible (of course for the better sound/video quality).  However, when it comes to a conflict, the recording rules are not working quite right.

Let's use Hell's Kitchen as an example.  Hell's Kitchen plays on Channel 55.1 through Digital, or channel 7 for analog.  The recording is set to "find and record one showing of this title each week".  In addition, the preferred input is set to "Digital" so it will record on the digital input.  Also note that this recording rules was originally setup using the digital 55.1 channel.

Now, I save the schedule and go look at the Upcoming Recordings.  In there, it shows that the specific showing that I made the recording rule on records on the Digital input.  But, then every single other showing uses the Analog input.

When opening the other showings, they all show the preferred input is set to Digital - but they still don't use it.

Anyone have any insight on why this is occurring?  Both the Digital and HVR-1600 inputs have an input priority of 1 while the PVR-150 has an input priority of 0.

---

### Post by blackoper on 2009-10-06
I just go through and edit the channel priority in mythweb to a higher value for the digital/hd channels. Seems to work for me after doing that. Analog channels have a 0 priority. Digital channels I like have a 1, and HD digital channels have a 2

---

### Post by bsntech on 2009-10-07
Thank you for your input on that.

Believe it or not, I found the channel priorities a bit after posting this - and I did the exact same thing you did (minus the HDTV channels).  Al digital have a priority of 1 and analog 0.  That didn't seem to make a difference though.

---

