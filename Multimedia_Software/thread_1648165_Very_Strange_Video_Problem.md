---
title: "Very Strange Video Problem"
date: 2010-12-18
forum: Multimedia Software
---

### Post by Uruz on 2010-12-18
Today, I copied some videos from my network's storage array to watch on my computer. When I opened a video in VLC, the window sized to fit the dimensions and audio began to play, but the video was blank. I checked preferences and nothing had been changed since the last time I watched a video in VLC. I opened the video in Movie Player and received an error "Can't play a text file without video or visualizations." (likely referring to the subtitles)

I assumed that this must be caused by the video itself, but when I tried playing other videos which I had previously watched, the same thing happened.

I **know** it's not a problem with the video files themselves, since it has happened on videos which I had previously viewed without problem.

Side note: I recently switched to an Nvidia graphics card and am using the corresponding drivers.

This has happened with .ogm, .avi, and .mkv, as well as FlashVideo downloaded from Youtube (where it worked without problem)

Anyone have ANY ideas?

Thanks for you help,
Uruz

---

### Post by coldfire82 on 2010-12-18
> **Uruz said:**
> Today, I copied some videos from my network's storage array to watch on my computer. When I opened a video in VLC, the window sized to fit the dimensions and audio began to play, but the video was blank. I checked preferences and nothing had been changed since the last time I watched a video in VLC. I opened the video in Movie Player and received an error "Can't play a text file without video or visualizations." (likely referring to the subtitles)

I assumed that this must be caused by the video itself, but when I tried playing other videos which I had previously watched, the same thing happened.

I **know** it's not a problem with the video files themselves, since it has happened on videos which I had previously viewed without problem.

Side note: I recently switched to an Nvidia graphics card and am using the corresponding drivers.

This has happened with .ogm, .avi, and .mkv, as well as FlashVideo downloaded from Youtube (where it worked without problem)

Anyone have ANY ideas?

Thanks for you help,
Uruz

hmmm, should be a driver problem. No other clues. Maybe check their documentation of other pre-requisites

---

### Post by Uruz on 2010-12-18
> **coldfire82 said:**
> hmmm, should be a driver problem. No other clues. Maybe check their documentation of other pre-requisites

Problem solved! You were right, it was caused by the drivers. I asked my brother and he said something about VLC not using my card and rendering the video in the wrong hardware. I went into VLC's video options and changed the output to a setting that looked familiar and it worked!

Thanks for our help!

---

