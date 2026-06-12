---
title: "How do I get channels with Plextor ConvertX PX-TV402U?"
date: 2008-05-17
forum: Mythbuntu
---

### Post by mixersoft on 2008-05-17
I finally have Mythbuntu 8.04 installed (downgraded to the 2.6.24-1 kernel), plus all the drivers for the Plextor ConvertX are loading properly.

Not all I need to do is to tune channels for AFN. I think I read somewhere that Scan Channels is not supported, so I set the mythtv backend to use NTSC-Cable from the Tuner, and loaded the AFN channels from SchedulesDirect. But when I go to watch LiveTV, I only get green static.

Has anyone got this thing working on Mythbuntu 8.04?

---

### Post by bwilson on 2008-05-25
I have it working in Gutsy PPC. Maybe this will help...

Make sure the Recording Profiles for the Plextor set the Width/Height to 640x480. I also found that I had to set the audio sample rate to 32000 (a couple screens after the Width/Height settings) or the audio was all crunchy.

Also, make sure that you have connected the Tuner input for the Plextor to your SchedulesDirect feed in mythtv-setup.

---

### Post by mixersoft on 2008-05-26
I actually changed it to 720x480, and it seemed to work fine. I choose that value because it said it was "NTSC standard". But that doesn't seem like a 4x3 screen.

From what I can gather on the web, 720x480 is DVD/NTSC resolution, so I guess 640x480 is TV/NTSC, is that right? 

Am I wasting HD space/bandwidth by recording at 720x480?

---

### Post by bwilson on 2008-05-26
I don't know for sure, but I think the limiting factor will be the bitrate that is set in the Recording Profile.

---

