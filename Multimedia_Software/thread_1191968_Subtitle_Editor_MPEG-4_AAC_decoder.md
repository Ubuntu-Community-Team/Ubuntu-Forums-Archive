---
title: "Subtitle Editor: MPEG-4 AAC decoder"
date: 2009-06-19
forum: Multimedia Software
---

### Post by chmacka on 2009-06-19
I can't open .mp4 file in Subtitle Editor:

[I]GStreamer plugins missing.
The playback of this movie requires the following decoders which are not installed:

MPEG-4 AAC decoder[/I]

Where can I download MPEG-4 AAC decoder?

---

### Post by starcraft.man on 2009-06-19
> **chmacka said:**
> I can't open .mp4 file in Subtitle Editor:

[I]GStreamer plugins missing.
The playback of this movie requires the following decoders which are not installed:

MPEG-4 AAC decoder[/I]

Where can I download MPEG-4 AAC decoder?

Have you installed ubuntu restricted extras? I'm pretty sure gstreamer can handle this. Open a terminal and type in "sudo aptitude install ubuntu-restricted-extras" then push enter. Terminal can be found at Applications > Accessories > Terminal.

If you've done the above, gstreamer should have all the codecs it needs for video and subtitles unless it's a problem with the program.

---

### Post by Revolutionary101 on 2009-06-19
You could also open up Add/Remove Programs in the Applications menu. 

Then just search for gstreamer. Then install all of those codecs or just the MPEG-4 and AAC ones.

---

### Post by chmacka on 2009-06-19
> **starcraft.man said:**
> sudo aptitude install ubuntu-restricted-extras
This worked. Thanks!

---

### Post by starcraft.man on 2009-06-19
> **chmacka said:**
> This worked. Thanks!

Your most welcome, have fun and don't be shy. We don't bite... much. ;)

---

### Post by alexelprogramador on 2012-06-22
> **starcraft.man said:**
> Have you installed ubuntu restricted extras? I'm pretty sure gstreamer can handle this. Open a terminal and type in "sudo aptitude install ubuntu-restricted-extras" .


hey! many thanks.

It runs for me!

 I have backtrack5 r1

I can see now downloaded videos from youtube!! :guitar:

---

### Post by dandan4000 on 2012-10-18
I tried this on my laptop, but the player still says that MPEG-4 AAC is still not installed. What's wrong?

---

