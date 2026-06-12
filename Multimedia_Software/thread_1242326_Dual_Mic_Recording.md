---
title: "Dual Mic Recording"
date: 2009-08-17
forum: Multimedia Software
---

### Post by Forbees on 2009-08-17
i'm trying to find a program that supports two mics at the same time for recording and editing

i'm currently running windows 7, but if there is only a linux program that edits and records dual mic i can get ubuntu back on here

i have two sound cards, but one mic isn't working so right so i plan on just using the Mic and LineIn for my two mics

i understand that there is a box or something you can buy to mix them in, but i want to be able to edit each mic separately

ideally i want to plug my guitar in to my computer and a mic so i can record my singing and mic at the same time, and have two separate tracks to edit

---

### Post by Crispian Troy on 2009-08-17
I am trying to record sound on my computer by using a dual male 1/8" jack in my computer using the headphone and mic jacks on my laptop. I was told that this would work, and I tried using Windows Sound Recorder to do this but the quality came out terrible, sounding like a static-y radio station. I already tried adjusting the volume on both the computer and the source of the sound, but no luck.

---

### Post by Forbees on 2009-08-18
i thought about getting a dual 1/8th adapter . .  but than in the recording program that would only show up as one audio track . . . which would make editing very hard

---

### Post by bobince on 2009-08-18
> **Forbees said:**
> i plan on just using the Mic and LineIn for my two mics

Most sound cards won't let you record from two sources at once (they don't have the ADC hardware).

Probably the easiest route for specifically two mics is to use a little 2xMono->1xStereo jack adaptor to plug them into the same mic socket (or line-in depending on the levels you get out... I used a small cheap pre-amp to boost mics to line as my sound card mic input quality was pretty poor). You then get a stereo recording with one source in each channel, which is easy to split back into mono signals.

For more than two sources it starts to get tricky. Running multiple audio devices (like sound cards, or USB mics) introduces desynchronisation between them, as their clocks never run exactly in sync. You can get single audio devices with many inputs you'll be able to record from at once, but this is prosumer kit and typically costs a bit.

If you don't need your recordings perfectly synced, you can just run multiple simple recording programs and set each to record from a different sound card (eg. under Linux you might try two gnome-sound-recorders, with a padevchooser to move the streams to differing devices). You can then arrange the results in a multitrack editor and resample them if necessary to correct for sync drift.

It's a shame there isn't software (that I know of on Linux or Windows) that will record from multiple sources in one program, and resample them to sync automatically; doing it manually is a pain. There is a hack that can be done with configuring ALSA to route multiple devices as a ‘virtual device’, but it's a bit of a pain to set up and without any resampling you get little clicks where the sync fails.

Support for multiple audio devices kind of sucks, in both Linux and Windows. (Maybe Mac too, I haven't looked.)

---

### Post by Forbees on 2009-08-18
i didn't realize said adpater woult make it stereo like that  . . so technically thats all i need i think :)

but if it helps, i DO have two soundcards, so if said program was around i should beable to do it. . . . .

thanks though, not the answer i'm looking for but it does solve the problem

---

