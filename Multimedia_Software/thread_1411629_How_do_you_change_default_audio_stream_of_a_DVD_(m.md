---
title: "How do you change default audio stream of a DVD (maybe edit IFO)?"
date: 2010-02-20
forum: Multimedia Software
---

### Post by Darin on 2010-02-20
Hi. I just had a quick question. I would like to burn a DVD to disc. The VOBs in the Video_TS folder have 3 Audio tracks: Stereo, Surround, Mono. By default it plays the Stereo track. Is there any way to change this?

ffmpeg -i [insert_video_location] in the terminal gives me:
```

Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s
Stream #0.2[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Stream #0.3[0x82]: Audio: ac3, 48000 Hz, mono, s16, 96 kb/s

```

Will 0x80 always be the default? Normally this wouldn't be a problem, but I'm going to be playing these discs on a DVD Player without a remote (can't help it), so I won't be able to switch the audio on the fly, and they have no menus. You put it in, and it goes straight to the movie.

I read the defaults may be set in the IFO file, but I'm not sure.

Does anyone know if this is possible? Thanks for anyones help!

- Darin

---

### Post by Darin on 2010-02-20
Hey, I figured it out! I used a program called PgcEdit. It's pretty straight forward, but there is a tutorial on the page as well. It's available for all OSes, with a Linux Executable even. Very easy.

[Link to: PgcEdit Homepage]("http://download.videohelp.com/r0lz/pgcedit/")
[URL="http://forum.digital-digest.com/showpost.php?p=296707&postcount=1"]
Link to: Audio Stream Tutorial[/URL]

Basically, you just open PgcEdit, open the DVD directory, select the main title on the left side, double click or hit Edit PGC, set the audio stream order, hit OK, hit Save DVD. That's it. You can find out the types of audio streams if you're not sure by using 'ffmpeg -i [insert_video_location]' in the terminal, like in the post above.

It does leave a PGC_backup folder in your VIDEO_TS directory, but you can delete it as far as I can tell.

Pretty easy, I just didn't know where to look. I'll have to try to donate. Anyway, hope this helps someone else.

- Darin

---

### Post by mc4man on 2010-02-20
PgcEdit is a great program, even though there is a linux version I use the win. one in wine - the interface is so much better, like night and day  (the things it can do are quite unique to say the least..

---

