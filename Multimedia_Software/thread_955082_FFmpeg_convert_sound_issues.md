---
title: "FFmpeg convert sound issues"
date: 2008-10-21
forum: Multimedia Software
---

### Post by mcgooie on 2008-10-21
I am trying to convert a 24fps avi file into an mpeg file. I have installed ffmpeg from medibuntu and am trying to use the WinFF GUI for the converting.

I can get the files converted ok with the picture perfect however the sound is slightly out of sync - if i skip forward about 15mins into the video its off by about half a second or so.

Does anyone have any ideas?

Thanks

---

### Post by mcgooie on 2008-10-22
Ive tried to simplify things by using the CLI and this command:

ffmpeg -i InputFile.avi -target pal-dvd OutputFile.mpeg 

This also results in the sound being out of sync, has anyone out there been able to successfully convert an avi to mpeg?

---

### Post by FakeOutdoorsman on 2008-10-22
You might look into vsync and async:
> `-vsync parameter'
Video sync method. Video will be stretched/squeezed to match the timestamps, it is done by duplicating and dropping frames. With -map you can select from which stream the timestamps should be taken. You can leave either video or audio unchanged and sync the remaining stream(s) to the unchanged one. 

`-async samples_per_second'
Audio sync method. "Stretches/squeezes" the audio stream to match the timestamps, the parameter is the maximum samples per second by which the audio is changed. -async 1 is a special case where only the start of the audio stream is corrected without any later correction.
I've never used them before so I can't give any usage examples.

---

