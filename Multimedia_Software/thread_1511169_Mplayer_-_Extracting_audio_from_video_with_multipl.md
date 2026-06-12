---
title: "Mplayer - Extracting audio from video with multiple tracks"
date: 2010-06-16
forum: Multimedia Software
---

### Post by TheChaos0 on 2010-06-16
EDIT: Now I remembered. It's as simple as adding -aid and number of the track you want to extract.](*,) Duuur :)

```
mplayer "$INPUT" -aid 1 -ao pcm:fast:file=audio.wav -vc null -vo null
```

-----------------------------------------------------------------------------------------------------------------------

I guess this goes here.

I made a shell script for covering ogm, mkv, ect files into avi, while preserving subtitles. I only just realised that it only extracts the default audio track. Here's the part in question:

```
mplayer "$INPUT" -ao pcm:fast:file=audio.wav -vc null -vo null
```

It muxes the audio file into the converted avi afterwards, so that sound timing is preserved properly.

Question here is, how do I make it extract track 2 or 3 or etc, instead of default track. I feel like I knew the answer but I don't seem to remember, I looked through mplayer manual but I must have missed it.

Thanks.

---

