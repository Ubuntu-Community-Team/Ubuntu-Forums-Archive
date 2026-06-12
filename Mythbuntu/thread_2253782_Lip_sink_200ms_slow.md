---
title: "Lip sink 200ms slow?"
date: 2014-11-22
forum: Mythbuntu
---

### Post by AlecJ on 2014-11-22
Hi

Have been having problems with lip sink for a some time now,
wondered if it just me or a known issue?
Live TV and recordings are 200 mS too slow on all 12 tuners, dvb-T and dvb-S.

But dvd and videos from the hard dive are not, so I'm forever changing the audio sync.

Also having problems with the sound card "forgetting" it's 5.1, the fix is to ssh in and use alsamixer, then by toggling 4 to 6 channels, brings the full sound back?
This is only after a reboot, having to do more and more hard resets as the system has started freezing after the last kernel upgrade. normally after a long periods of inactivity.

don't get this problem on the remote laptops, just the main backend/frontend.

any thoughts?

mythbuntu 12.04.? the latest 64bit, 6 core amd cpu, onboard Nvidia sound card and 6 tuner cards
using fixes/0.27

---

### Post by AlecJ on 2014-11-24
Is there a setting for this as it only applies to the main frontend backend not to the remote laptops?

---

### Post by dannyboy79 on 2014-11-24
if it's only happening on the primary backend which is also a frontend than I would assume it's just too much for the machine to handle so the audio/video loses sync. if you can watch the same video on a remote frontend and the audio/video is in sync than i would strongly suggest getting a dedictaed frontend to sit next to your backend because you're simply trying to do too much on the system at once. that's just a hunch though

---

### Post by AlecJ on 2014-11-25
it's quite powerfull
AMD FX(tm)-6100 Six-Core Processor 1400.000 MHz
8Gb Ram
6Tb storage

Don't get any slow downs even when it's busy recording 8 programs simultaneity, ripping a DVD and live tv. well thats not quite true do get slight disturbance when a recording starts in the background, but not during or as it stops.
it's still 200ms slow from all tuners but not from dvd file playback, even when it's only doing live tv.

It's just a nuisance changing the sync. I don't get why it's doing it?

---

### Post by Lester_Burnham on 2014-11-25
Hi,
Have you tried a different video playback profile, just to rule it out.
Setup>video>playback (2nd or 3rd page at the top)
Lester

---

### Post by AlecJ on 2014-11-26
Thanks for the pointers

The lip sync does indeed change as the profile is changed 

I'm using VDPAU high quality

tried a few changes but the loss of picture quality pushed me back to VDPAU

so editing VDPAU to use max of 4 CPU's from 1 seems to have helped, I think?

I've gone a bit bug eyed trying to see the difference now

will see what happens

---

### Post by dannyboy79 on 2014-11-26
your playback profile will definitely matter. :)  I had assumed you already looked at that. hope you got it sorted out

---

### Post by Lester_Burnham on 2014-11-26
> **AlecJ said:**
> Thanks for the pointers

The lip sync does indeed change as the profile is changed 

I'm using VDPAU high quality

tried a few changes but the loss of picture quality pushed me back to VDPAU

so editing VDPAU to use max of 4 CPU's from 1 seems to have helped, I think?

I've gone a bit bug eyed trying to see the difference now

will see what happens

Hi,

I have noticed the same audio sync issue the last week or 2.
I also think someone on the mailing list had bought this to JYA's attention.

Here's one bug, not sure if it is the actual one though.
[https://code.mythtv.org/trac/ticket/12027](https://code.mythtv.org/trac/ticket/12027)

It did mention it was only with VDPAU too.
Hmm. That's interesting though, because the first time I really noticed it, was using UPNP streaming a recording to a Toshiba TV.

Lester

---

### Post by AlecJ on 2014-11-26
been watching tonight and it's much better, still goes out at times I think
 funny how when it's behind you can see it and it's annoying, but when it's in front it makes you feel dizzy. 

the audio sync is back to 0 now and nothing was said by the watching parties.

---

