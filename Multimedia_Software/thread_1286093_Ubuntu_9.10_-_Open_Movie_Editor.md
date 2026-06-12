---
title: "Ubuntu 9.10 - Open Movie Editor"
date: 2009-10-08
forum: Multimedia Software
---

### Post by ColinG on 2009-10-08
Installed Open Movie Editor via Synaptic (it was already in the repositories), ran it and imported some video (dv) clips captured via Kino. The vid played fine but there was no sound. Terminal output was:
OpenGL version string: 1.4 Mesa 7.6 
GL_MAX_TEXTURE_SIZE = 2048 
----8<----------------------- 
[pcm_s16le @ 0xb29b1d0]buffer smaller than AVCODEC_MAX_AUDIO_FRAME_SIZE 
    Last message repeated 951 times 
[pcm_s16le @ 0xb2d4650]buffer smaller than AVCODEC_MAX_AUDIO_FRAME_SIZE 
    Last message repeated 381 times 
[pcm_s16le @ 0xb29b1d0]buffer smaller than AVCODEC_MAX_AUDIO_FRAME_SIZE 
    Last message repeated 1603 times 
[pcm_s16le @ 0xb2d4650]buffer smaller than AVCODEC_MAX_AUDIO_FRAME_SIZE 
    Last message repeated 381 times 
[pcm_s16le @ 0xb29b1d0]buffer smaller than AVCODEC_MAX_AUDIO_FRAME_SIZE 

Also, playback in Rythmbox was affected, when playing MP3 I got the codec needed report when all had been well prior to installing Open Movie Editor. The complete removal of OME has put everything back to right but clearly something is amiss.

Any ideas in Ubuntuland?

Thanks
Colin

PS - Karmic is looking really good.

---

