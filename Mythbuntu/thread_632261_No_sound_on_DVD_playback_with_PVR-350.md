---
title: "No sound on DVD playback with PVR-350"
date: 2007-12-05
forum: Mythbuntu
---

### Post by therealbrewer on 2007-12-05
I've got the audio out of my PVR-350 connected to the line in of my on-board sound. Live TV and recordings work fine. I also have X routed through the TV-out of the PVR-350 so that I can switch desktops and see the X session on the TV. The option "TV audio through PVR-350 only" is not selected by the way. I've got all the mixer sliders turned up except for mic. Lastly, If I switch away from myth to the regular desktop and open the dvd with VLC player, for instance, then sound is OK.

Any ideas?

---

### Post by andrewb78 on 2007-12-21
I don't have my sound set up like you do, but you might try checking "TV audio through PVR-350 only" and seeing if you are satisfied with the result.  Since you have wired the sound from the TV Out on the PVR-350 to your sound card, you should get sound when you check that option.  There might be a problem with controlling the sound with the remote, etc., that makes this option unsatisfactory.  In that case, I would check the audio output device, which you can find at Utilities/Setup -> Setup -> General on about the third screen.  Do you know what ALSA device you are using to get sound from your regular desktop applications?  Are your speakers connected to some sort of SPDIF output instead of a normal output?

Let me know if any of this works.

---

### Post by axelsvag on 2007-12-21
I don´t have the 350 but at some dvd:s I got the same problem. Perfect sound at the dvd menu but noting when you start the movie. If I play through the desktop everything is perfect. I hope someone found an answer?

---

### Post by jjlllk on 2008-06-22
I have the same problem with Mythbuntu 8.04. Running a PVR-350 with tv-out setup on PAL-TV. I have no sound on DVD with Internal player, picture is fine. I can watch DVD with VLC outside Frontend on TFT Monitor as second screen just fine.
Any suggestions ????
What would be an alternate setup for Internal in the video playback config ???
Should I go for xine as output on PVR-350(Tv-out) ???

---

### Post by trubblemaker on 2009-02-15
I have the same problem did anyone find a fix for this?

---

### Post by trubblemaker on 2009-02-15
If it helps this worked out for excellent quality playback as well as sound via pvr 350

set dvd playback to :
```
xine --no-splash --auto-play=fhq --auto-scan dvd
```

---

