---
title: "acidrip crops to 688?"
date: 2012-02-03
forum: Multimedia Software
---

### Post by qwertyjjj on 2012-02-03
I have a DVD that when played from disc fills the whole screen.
However, when I select the crop in the video settings to rip it, it selects 688. I changed it in the scale to try and scale it up but it won;t go above 1000.
My screen resolution is 1280x720.
Is there anyway, I can get the correct setting for the DVD?
Also, to get the bits/px above 0.2, the file size for s simple 50min episode needs to be avove 700Mb - isn't this a lot?

---

### Post by qwertyjjj on 2012-02-05
any ideas on what I can try?

---

### Post by mcduck on 2012-02-05
So you are trying to make a DVD, playable on a normal DVD player (or rip such DVD)?

DVD Video format doesn't support HD resolutions, so you are not going to get 1280x720 (720p) on that format. The resolution on a movie DVD is 720x480 (480i/480p/NTSC) or 720x576 (576i/576p/PAL).

What comes to file size, that's really a question of what compression is used, and the quality. IF yua re trying to create a DVD, the only compression allowed is rather old MPEG2 so you'll end with large files. And if you are trying to rip one, try using a more modern compression, like MPEG4 or H.264 instead.

---

### Post by qwertyjjj on 2012-02-05
> **mcduck said:**
> So you are trying to make a DVD, playable on a normal DVD player (or rip such DVD)?

DVD Video format doesn't support HD resolutions, so you are not going to get 1280x720 (720p) on that format. The resolution on a movie DVD is 720x480 (480i/480p/NTSC) or 720x576 (576i/576p/PAL).

What comes to file size, that's really a question of what compression is used, and the quality. IF yua re trying to create a DVD, the only compression allowed is rather old MPEG2 so you'll end with large files. And if you are trying to rip one, try using a more modern compression, like MPEG4 or H.264 instead.

But when I try to rip the DVD to AVI and select a res of 720, it still ends up as a square on the screen?
Is this because of the auto detect crop size?

---

### Post by mcduck on 2012-02-05
> **qwertyjjj said:**
> But when I try to rip the DVD to AVI and select a res of 720, it still ends up as a square on the screen?
Is this because of the auto detect crop size?

DVD video doesn't really have a "true" widescreen format at all, the widescreen on DVD is anamorphic (meaning it's a square image which is then stretched to the widescreen aspect ratio). I haven't used acidrip myself, but check if there's some setting for aspect ratio or anamorphic format available...

(and like I said, DVD Video format doesn't support HD resolutions such as 720p)

---

### Post by qwertyjjj on 2012-02-05
> **mcduck said:**
> DVD video doesn't really have a "true" widescreen format at all, the widescreen on DVD is anamorphic (meaning it's a square image which is then stretched to the widescreen aspect ratio). I haven't used acidrip myself, but check if there's some setting for aspect ratio or anamorphic format available...

(and like I said, DVD Video format doesn't support HD resolutions such as 720p)

But almost every DVD I come across on the net is encoded into a 720 format?
Also, some DVDs come in widescreen format don;t they?

---

### Post by mcduck on 2012-02-06
> **qwertyjjj said:**
> But almost every DVD I come across on the net is encoded into a 720 format?
Also, some DVDs come in widescreen format don;t they?

They must be BluRAY or HD-DVDs then. [DVD Video]("http://en.wikipedia.org/wiki/DVD-Video#Frame_size_and_frame_rate") is a standard resolution format.

Also keep in mind that 720x576 is not the same as 720p (which would be 1280x720 resolution).

And like I said, the widescreen image on DVD's is [anamorphic widescreen]("http://en.wikipedia.org/wiki/Anamorphic_widescreen"), created by squeezing the widescreen image to standard 4:3 aspect ratio on the disc, and then stretching it back to 16:9 when playing ack the video.

---

