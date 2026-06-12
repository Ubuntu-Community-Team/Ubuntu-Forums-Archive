---
title: "sound issues after upgrade to karmic"
date: 2010-01-05
forum: Multimedia Software
---

### Post by kongekrabben on 2010-01-05
Hi!

After i upgraded to karmic i experienced that the sound of spotify was at times strange. When i started a new song there was some strange plucking sounds, can most be understood as the sound a old LP-player makes when there is dust on the record. Not much but more than enough that I can hear it and wish it wasn't there. After some time of playing the songs sometimes was totally distorted by "disturbance" and it became impossible to even hear that there was a song there. Like when you are out of reception of a radio channel. 

I did some research and upgraded to the wine1.2 with "custom" pulsaudio drivers. Then the total distortion was gone, but the, always present, plocking sound still was there. I have tested adjusting PCM volume, have some volume on mono, upgrading to newer pulsaudio drivers. 

The same problem is when ever my dear computer i producing sound. Spotify, firefox, rythmbox and mplayer. 

It drives me mad. plx help me. I can't see any answers after spending some time on google. I hoped i could fix this without deleting and removing pulsaudio. 

Thx for any answers!

---

### Post by antientropy on 2010-01-11
Hi.

I had the same problem and got around it by changing the sound driver in use from winecfg's audio tab. I unchecked the ALSA driver and then checked the OSS driver, and changed hardware acceleration to basic. This fixed both the plucking sound and the distortion problem. Hope this helps!

---

