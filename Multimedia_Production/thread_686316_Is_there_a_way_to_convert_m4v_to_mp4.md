---
title: "Is there a way to convert m4v to mp4?"
date: 2008-02-03
forum: Multimedia Production
---

### Post by absolut1983 on 2008-02-03
Hello, folks.

   Does anyone know something that I can use to convert m4v files to mp4 so I can play them on my Walkman?

   Thanks a million.

---

### Post by eye208 on 2008-02-03
If the M4V file was downloaded from iTunes, it is probably DRM-protected (i.e. encrypted). As far as I know there is currently no way to remove the protection.

Edit: Can you play the M4V with a media player on Linux?

---

### Post by absolut1983 on 2008-02-03
Yes, Movie Player plays it, since it's just an episode of Diggnation that I downloaded via Miro.

---

### Post by eye208 on 2008-02-03
Unless there is DRM involved, M4V and MP4 are actually the same container format. If you can't make the files work with your walkman by simply changing the extension to .mp4, it is probably because the stream compression format inside the container is not supported by your walkman.

I can only guess here: The files probably contain H.264-compressed video but your walkman can handle MPEG-4 ASP or SP only (also known as Xvid/DivX). Maybe your walkman can't handle AAC audio either, only MP3.

You can use Avidemux to change the stream formats. Choose Xvid for video, "Copy" for audio and MP4 as a container for the output file. If the result is missing audio on your walkman, try again with LAME for audio. If video still doesn't work, try disabling some advanced options in the Xvid codec.

What brand/model is your walkman?

---

### Post by absolut1983 on 2008-02-04
Thanks for the help so far, man.

   My Walkman is the A818 (open platform). I tried to change the extension from m4v to mp4 and nothing happened, so I reckon Avidemux is all I have.

---

