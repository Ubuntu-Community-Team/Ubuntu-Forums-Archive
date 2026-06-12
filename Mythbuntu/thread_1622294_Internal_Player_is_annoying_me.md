---
title: "Internal Player is annoying me"
date: 2010-11-15
forum: Mythbuntu
---

### Post by LowSky on 2010-11-15
If I watch a recording from mythtv I get stuttering of playback and lines going through the video from time to time. All recordings are HD of 720P or 1080i.

Using Mythtv .24 with VDPAU (Nvidia 260.19.12 driver on a Nvidia 460 GTX)

If I watch the same recording from VLC it plays fine, If I play the file from my PS3 it plays fine. So I know it isn't an I/O issue or the hard drives failing.

The issue has to be with the Internal player.

I checked my frontend log and and same error I keep seeing 
```
ALSA, Error: WriteAudio: buffer underrun
```

Im guessing this is my underlying issue. Anyone know the fix?

---

### Post by managementboy on 2010-11-16
have you checked the audio settings? after an upgrade to 0.24 you need to rescan your alsa devices.

---

### Post by LowSky on 2010-11-16
Yeah I figured it out last night. For whatever reason MythTV was trying to use PulseAudio...switched it back to ALSA and to the correct hardware and it works fine, video and sound have improved.

---

