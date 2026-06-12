---
title: "Zoom to width rather than height"
date: 2009-09-08
forum: Mythbuntu
---

### Post by mungewell on 2009-09-08
Hi,
I'm using mplayer in my myth setup, however when view content originally from a wide screen VCR input I get a 'post box' view with black bars on top/bottom (included within the video image) and on the sides (imposed by mplayer).

Is there a way to instruct mplayer (or internal player) to 'fullscreen' to the width of the video to the width of the screen (and thus cropping off the redundant black bars on top and bottom)?

Video source is standard PAL, so I guess the proportions are known at least.

Cheers,
Mungewell.

---

### Post by mungewell on 2009-09-09
I discovered a fix which may be able to help. Using the mplayer filter '-vf crop=702:390:0:62' which will crop the top/bottom black bars off and enable full width fullscreen.

Obviously this is only settable on the mplayer command line, but what I am attempting to achieve is to watch 'live' the composite input of the card, so I can set up two new menu options to start mplayer with/without the cropping.

Mungewell.

---

### Post by no2498 on 2009-09-09
sounds like you nee to change to
16.9 or 4.3
in mplayer

---

### Post by mungewell on 2009-09-09
The image is not distorted, it just contains black bars at top and bottom which 'confuse' the fullscreen feature.

These are VHS tapes which I recorded between 10 and 5 years ago. I just like re-watching the old stuff, but am too lazy/disorganised to actual 'record' with the PVR-150 I have. Perhaps I should as the VCR's/tapes I have will not last for ever.

If I spec an aspect ratio, then the image will become distorted.
Mungewell.

---

