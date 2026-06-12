---
title: "MKV file stutters when playing in VLC"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by noremacyug on 2008-02-26
title mostly says it.  when playing a 720p MKV in vlc it stutters and doesn't play smoothly.  is there a codec pack i can download that will resolve this.

---

### Post by eye208 on 2008-02-26
> **noremacyug said:**
> when playing a 720p MKV in vlc it stutters and doesn't play smoothly.
It's probably an H.264-encoded HD movie, and your CPU is too slow to handle it.

> is there a codec pack i can download that will resolve this.
No, but you can transcode the video stream to a different format that is less demanding, e.g. Xvid.

---

### Post by noremacyug on 2008-02-26
before i switched to ubuntu i watched the exact same mkv files with winxp o.s. with no stutter and smooth playback.  i find it hard to believe it's my hardware.  it's certainly not the newest technology, but i know it is capable of handling a 720pmkv.

---

### Post by aeiah on 2008-02-26
whilst HD mkv files do playback ok in vlc for me, my pc is a lot more responsive when i play them with xine. perhaps you could try that.

---

### Post by noremacyug on 2008-02-26
> **aeiah said:**
> whilst HD mkv files do playback ok in vlc for me, my pc is a lot more responsive when i play them with xine. perhaps you could try that.

thanks, that made a huge difference.  problem solved!

---

### Post by chalewa on 2008-02-26
hm, i am going to have to try this as well. orginally i just chalked it up to my video card not being able to handle it.

---

### Post by noremacyug on 2008-03-06
well after not being able to get totem movie player to handle a dvd i've decided to give vlc another go.  it flawlessly handles my dvd's.  however mkv's still stutter.  are there any settings or codecs that can be installed to improve the playback?

---

### Post by soga_genzo on 2008-03-06
Try disabling FFmpeg's loop filter:

- Open the "Preferences" dialog and navigate to "Input / Codecs" -> "Other Codecs" -> "FFmpeg"
- Change the setting of "Skip the loop filter for H.264 decoding" to "All"

---

### Post by noremacyug on 2008-03-06
well, that certainly seemed to help, but still un-watchable to me.  how good are the restricted ati drivers?  i'm using them and am starting to think that perhaps that's the issue.  these files played perfect when i used winxp.

---

