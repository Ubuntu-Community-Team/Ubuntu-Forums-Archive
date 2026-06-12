---
title: "Recording Shows - Set to Record But Doesn't Show Up"
date: 2009-09-28
forum: Mythbuntu
---

### Post by bsntech on 2009-09-28
Hi all,

I just got the HVR-1600 card installed over the weekend.  The analog side of the card is much better than the current PVR-150 card I had as well.  The PVR-150 never had anything in stereo (always mono sound), but the HVR-1600 has better picture and also records in stereo on the analog side now.

For the ATSC/Digital tuner in the HVR-1600, I was able to pick up about 15 channels OTA - with a small antenna outside and no movement needed!

I did have one small problem though.  If you have both an HVR-1600 and a PVR-150, you may find out that the HVR-1600 analog card will not capture sound.  I had to change the order of the cards and put the PVR-150 above the HVR-1600 for the PCI slot order (PVR-150 is closer to the processor with the HVR-1600 just underneath).  Sound is now working.

However - I have one dilemma.

When I try to schedule shows on a digital channel, they never show up under Upcoming recordings.  If I record the same show on the analog tuner, it shows up normally.

I have both the PVR-150 and HVR-1600 analog tuners set to use the "Analog" Input group (this is so TV guide data is populated and I don't have a duplicate set of channels for these cards).  I then setup a "Digital" Input group for the digital side of the HVR-1600 tuner - so this group has the digital channels (3.1, 3.2, 12.1, 12.2, 12.3... etc)

I setup the HVR-1600 analog tuner with a higher priority than the other two cards - just because I want to ensure it is the default to get the better picture and sound over the PVR-150.

So, lets say that under the Analog group, there is Channel 12 - WILL.  Under the Digital group, there is Channel 12.1 - WILL-DT.

I will click on a show under MythWeb that is on channel 12.1 (also shows on channel 12 as it is the same station basically).  I will then set the program to always record on WILL-DT.

When I go into Upcoming Recordings, there is not one entry for this program.  However, if I only set it to record the program once, it DOES show up for that one recording.

Now if I click the program on Channel 12 and set the program to always record at anytime on WILL, it also DOES show up in Upcoming Recordings.

So, why will it not set a schedule to record all showings of the program on WILL-DT - but works just fine if I set it to record all showings of the program on WILL?  Of course, I would prefer the digital quality/sound of the show to record but it just won't take.

Thank you!

---

### Post by bsntech on 2009-09-28
Tried two other things:

Went into the Backend and set both HVR tuners with an input priority of 1 (PVR-150 set at 0).  The digital was originally set at 0 and the analog side of the HVR-1600 was set at 1 - but both are now set as 1.

This still didn't fix the problem.  Tried again to set a recording to record anytime on channel WILL-HD and none showed in the upcoming recordings.

I then set a manual schedule to record a timeframe everyday on the channel - and it WORKED!  But, why does it have to be manually set instead of the guide automatically setting to record those programs?

On another note - I set another program - CSI NY - to record anytime on a digital channel - and it worked just fine and chose that station over the analog station.  So I guess I'm just not understanding why it seems to only be with certain programs.

---

### Post by newlinux on 2009-09-28
My first thought is maybe there is some bad guide data? Or corruption in the database with the guide information? Sorry that's not much help.

---

### Post by bsntech on 2009-09-29
One more thing I noticed.

In MythTV itself under upcoming recordings, the TV recordings I have scheduled show up in gray and say that the showing won't be recorded because:

"This showing will not be recorded because this episode was previously recorded and is still available in the list of recordings".

---

### Post by bsntech on 2009-09-29
FIXED:

I got this fixed just a moment ago.

I went into the recording options and set it to NOT check for duplicates.  After doing so, they all show up now.

---

