---
title: "TV Picture really slow with pvr150"
date: 2009-07-16
forum: Mythbuntu
---

### Post by taffey01 on 2009-07-16
Howdy,
I've just installed Mythbuntu 8.04 from cd and install went well. Only issue that i have is that the quality of the TV Picture on my Plasma is poor. It seems to be seconds behind and really slow. Audio is fine.
 
Setup:
Newish PC with Mythbuntu 8.04
Freeview Satelite decoder with composite connection to pvr150 card on PC.
DVI connection to Plasma TV from PC.
 
I've set the card as an MPEG2 card with PAL and New Zealand. I've tried PAL I and PAL BG and the satelite decoder is set for PAL/BG.
 
Is there something i can try to improve this quality as this works fine from Windows Vista MCE?????
 
Cheers guys!

---

### Post by klc5555 on 2009-07-16
> **taffey01 said:**
> Howdy,
I've just installed Mythbuntu 8.04 from cd and install went well. Only issue that i have is that the quality of the TV Picture on my Plasma is poor. It seems to be seconds behind and really slow. Audio is fine.
 
Setup:
Newish PC with Mythbuntu 8.04
Freeview Satelite decoder with composite connection to pvr150 card on PC.
DVI connection to Plasma TV from PC.
 
I've set the card as an MPEG2 card with PAL and New Zealand. I've tried PAL I and PAL BG and the satelite decoder is set for PAL/BG.
 
Is there something i can try to improve this quality as this works fine from Windows Vista MCE?????
 
Cheers guys!

Just a couple of things.

Mythtv will buffer the analog input for 3-5ish seconds. If you're running some kind of pass-through cable for the sound, rather than having the sound also go with the video through mythtv and then through the sound card (and then to the TV or speaker system), the video will always appear to be a few seconds behind the audio. Until you hook it up without the pass-through.

Picture quality on a PVR 150 isn't the best, even for analog, but after the thing has been set up on the backend, there are adjustments to make in the frontend: In the setup/tv settings/recording profiles/mpeg2 recorders, you can adjust the default resolution the thing is recording at. I don't know the defined resolutions for PAL, but on NTSC the setup defaults to a very grainy mid-quality resolution for recording (something like 480x480) which can then be tweaked up to a more reasonable 720x480 --check to see whether you can do something similar for the appropriate PAL resolutions.

Mythtv really prefers to have an NVIDIA GeForce graphics card with proprietary drivers installed. ATI is OK (usually, also with proprietary drivers); for analog or SD use, other completely open-source supported graphics (like Intel) are also fine. Make sure you have the best drivers available installed for your particular graphics setup. Depending on card/drivers (and whether you have enabled it in the frontend setup), you will have on-screen picture controls support both for recording and (cross your fingers) for playback.

Anyway, these are some initial things to look for.

---

### Post by taffey01 on 2009-07-16
Thanks for that i'll try some tweaking and see if it improves the quality.

---

