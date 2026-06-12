---
title: "Recorded audio streams won't play"
date: 2009-05-22
forum: Multimedia Software
---

### Post by sofasurfer on 2009-05-22
I recorded some streams from Shoutcast by using the sound recorder. When I play them back the progress bar moves but there is no sound. Any ideas what I should do to get them to play back?

---

### Post by andrew.46 on 2009-05-23
Hi sofasurfer,

> **sofasurfer said:**
> I recorded some streams from Shoutcast by using the sound recorder. When I play them back the progress bar moves but there is no sound. Any ideas what I should do to get them to play back?

Can you try to play the file with another application such as vlc?

Andrew

---

### Post by bobince on 2009-05-23
Have you checked the file in an audio editor (such as Audacity) to see whether there's actually any waveform there? ie. that you haven't just recorded a load of silence from the wrong input channel.

For SHOUTcast streams it's better to pick up the stream directly than send it through a player and record the results. This keeps the original full-quality stream data, without the potential quality loss of decoding, mixing and possibly re-encoding.

You can do this as simply as “wget [http://radio.example.com:8000/”](http://radio.example.com:8000/”), though as this simply dumps the raw stream you'd also have to be listening on another player to work out when to terminate the stream download. Alternatively VLC's ‘Convert/Save’ feature will let you listen to a stream whilst also dumping it to disc. Other, more involved programs will do the same but split the output by track metadata.

---

