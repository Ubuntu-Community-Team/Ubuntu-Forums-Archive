---
title: "how to get sound to be synchronized with video?"
date: 2009-02-15
forum: Multimedia Software
---

### Post by higashi on 2009-02-15
I have a few videos on my computer where the sound either plays too early or too late for the video. its extremely annoying. I was wondering if there's a way  i can fix that, & what would that 'way' be?

Please help me as soon as possible as i would like to get these videos onto my ipod today.

Thanks.

---

### Post by wolfen69 on 2009-02-15
i'm sure the videos themselves are fine. so go ahead and put them onto your ipod. it's just ubuntu screwing up the playback, which i'm not sure how to fix.

---

### Post by higashi on 2009-02-15
I did put them onto my ipod and they played the same way. This doesn't happen with all video's, just a few, so i'm assuming its the videos themselves. I now took them off of my ipod to fix them before putting them back.

---

### Post by binbash on 2009-02-16
You can sync the audio and video with avidemux

---

### Post by higashi on 2009-02-16
> **binbash said:**
> You can sync the audio and video with avidemux

Thanks but... how?

---

### Post by andrew.46 on 2009-02-17
Hi,

The commandline way is to player the video with MPlayer and use the + or - key to adjust the audio by +/- 0.1 seconds. Then copy the clip using FFmpeg and utilise -itsoffset with the resulting offset number. This would all be a little painstaking so you would need to be fairly keen :-).

Andrew

---

### Post by higashi on 2009-02-26
> **andrew.46 said:**
> Hi,

The commandline way is to player the video with MPlayer and use the + or - key to adjust the audio by +/- 0.1 seconds. Then copy the clip using FFmpeg and utilise -itsoffset with the resulting offset number. This would all be a little painstaking so you would need to be fairly keen :-).

Andrew

Thanks. i think i'll try that. but... i also have this video where the sound changes.. for example, it can be on time at one point, then late at another point, then early at another point. What do i do in this case?

---

### Post by andrew.46 on 2009-02-27
Hi higashi,

> **higashi said:**
> Thanks. i think i'll try that. but... i also have this video where the sound changes.. for example, it can be on time at one point, then late at another point, then early at another point. What do i do in this case?

I suspect that if the sync is varying so wildly there is not much you can do. I am always ready to be corrected though :-).

Andrew

---

