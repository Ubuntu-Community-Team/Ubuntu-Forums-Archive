---
title: "audio out of sync"
date: 2010-07-04
forum: Mythbuntu
---

### Post by Mad_Professor on 2010-07-04
Hello I have annoying problem that I've noticed this past week.

I had 9.04 before and never had any audio issues, when I upgraded to 10.04, I really didn't have time to test drive it. This past week I noticed in all my recordings my audio is out of sync with the video by 680+MS.

It also does this in Live TV.

I'm not sure how I can correct it.

Specs:
P4 2.6ghz
512MB PC133 sdram
1x 40GB
1x 200GB
2x 80GB
all in LVM totaling 300GB
1x ASUS saa7134 tuner
1x ASUS cx23880
Nvidia 6600GT AGP

---

### Post by newlinux on 2010-07-04
When you play your recordings with mplayer or VLC, is the audio still out of sync? How out of sync is it? Can you use the audiosync function in the front end to get it right (temporary solution).

Also you might want to check your frontend logs for clues (if it is playback related and not recording related).

---

### Post by Mad_Professor on 2010-07-06
Sorry went out of town for Independence day.

Anyways...
Can't get VLC to output any audio not sure what's wrong. I tried mplayer and the audio is synced up, I also noticed a message on backend in dmesg about cpu being throttled due to temps, I cleaned out the heatsink and fan, and tried mythtv again but it still out of sync, but mplayer, it's fine.

It also does it on second frontend,
This seems to be an issue with mythtv or my backend.
Audiosync from the menu works if I set it 650-700+ but I want a more permanent solution.

---

### Post by newlinux on 2010-07-07
Well, definitely sounds like a playback problem if mplayer plays the files fine. You might want to look at your frontend logs and play around with different playback profiles. Do you have "Use video as a timebase" enabled or any audio buffering? What hardware are you running and what type of content are your playing back (HD?). Do you have non recording files in mythvideo that give you the same problems.

There are lots of things that can cause this, thus all my questions :)

---

### Post by Mad_Professor on 2010-07-07
I think I solved it.

When I first setup mythbuntu 9.04 I had two tuners and only one sound card, they both require audio out via cable. After wrestling with the problem I found out that asus saa7134 had DMA sound input. After setting it up to feed through the pci, all I got was a chipmunk and it sucked. Later I found out that I had to set the sampling rate to 32000khz. So I did.

*Fast Forward to now with the upgrade of 10.04 and my current problem.*

After reviewing the frontend logs, I noticed it was Resampling the audio from 32000 to 48000khz. I went looking for something in the setup menu of the frontend and found under "General," where the alsa setup is, An option for advance alsa controls. I hit the check box and only two options were available, "Override SRS" and "Aggressive sound buffer."

I checked the box for Override SRS, which had 4 modes "BEST, GOOD, FASTEST, DISABLE" and I set it to disable, and now all my audio is in-sync with video including live TV.

---

