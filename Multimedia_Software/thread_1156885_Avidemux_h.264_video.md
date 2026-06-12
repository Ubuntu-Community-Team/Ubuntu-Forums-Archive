---
title: "Avidemux h.264 video"
date: 2009-05-12
forum: Multimedia Software
---

### Post by pokogr on 2009-05-12
Hi all,

Have anyone managed to convert a video with avidemux that is playable on iPhone 3g? If yes, can you post the settings you used?

I don't want to use another tool because I want to be able to embed subtitles in the movies. 

Regards,
Poko

---

### Post by djbushido on 2009-05-12
You can try using Handbrake to rip a dvd (and embed subtitles) and convert directly to h.264. Alternately, try using a video conversion tool (ffmpeg, mencoder, transcode - ffmpeg is the best bet for you probably - look at winff) after you have embedded the subtitles to convert it for iphone.
Avidemux is not a very good idea for trying to convert videos, look at another tool like mentioned above. One of those should work.

---

### Post by MepisReign on 2009-05-12
In my experience Handbrake is the way to go, Google for it, You will no regret it

Greetz!

MepisReign

---

### Post by pokogr on 2009-05-12
Hmmmm.... I don't want to have to embed the subs and then convert it to the appropriate format... Bummer ha?

---

### Post by djbushido on 2009-05-12
I honestly think that that is your best bet. Handbrake can also embed subtitles (as well as others) and then convert it.
However, if you're willing to give it a shot, mencoder could probably rip, embed, and convert all at the same time. The problem being that mencoder is an EXTREMELY complicated program.
Overall, if you have the time, I would highly recommend just ripping and converting as avidemux is not meant as a video converter - it is much more of a swiss army knife than, I don't know, a clay spinning wheel???? Someone want to help me with this metaphor? Point being that trying to convert with avidemux will be like trying to put the square peg in the round hole. Eventually it will fit because you broke the hole open, but it's a pain in the mean time.

Wow, that was a lot of rambling. Anyway, as stated above, your best bet is to rip and convert, not all at the same time.

---

### Post by pokogr on 2009-05-12
Wow, thanx a lot. I think I do understand what you just said. Never expected a metaphor in an avidemux thread. Ubuntu community keeps surprising me :)

Thanx again mate,
Regards

---

### Post by djbushido on 2009-05-12
Not a problem. And metaphors? I'm just nice...

Anyway, to get some conversion help for you try to install these packages - ffmpeg, libx264, libavcodec51-unstripped (or something like that) and winff (available [here]("http://winff.org/html/")). Winff should have some presets available for iPod devices, and should allow you to convert videos.
Also, if you have the dvd's (preferably unencrypted) then you can use Handbrake to rip the dvd to your format of choice. You will need libdvdcss among others, and if you don't have that set up, let me know.
Post back any more questions, etc.

---

### Post by pokogr on 2009-05-12
I'll try your suggestions and if anything arises I'll let you know.

I appreciate your help, thank you very much.

Regards,
Poko

---

