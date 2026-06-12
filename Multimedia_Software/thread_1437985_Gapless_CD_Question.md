---
title: "Gapless CD Question"
date: 2010-03-24
forum: Multimedia Software
---

### Post by djbushido on 2010-03-24
So I recorded a dj mix of myself, and I have written down when the tracks changed. Currently there is an audio file of all the tracks put together. Instead of burning said file, I was hoping to get a cue sheet that I could skip between songs on the cd player, yet keep gapless playback. I'm pretty sure this would be possible, I just am not sure how. Anybody have any ideas?

---

### Post by Chronon on 2010-03-24
> **djbushido said:**
> So I recorded a dj mix of myself, and I have written down when the tracks changed. Currently there is an audio file of all the tracks put together. Instead of burning said file, I was hoping to get a cue sheet that I could skip between songs on the cd player, yet keep gapless playback. I'm pretty sure this would be possible, I just am not sure how. Anybody have any ideas?

You can make your own cue sheet.  It's just a text file.
[http://en.wikipedia.org/wiki/Cue_sheet_%28computing%29](http://en.wikipedia.org/wiki/Cue_sheet_%28computing%29)

---

### Post by djbushido on 2010-03-25
Ah, but I found an easier way!
You will need audacity, a program called label2cue, another called shntool, and wodim (in cdrkit).
Fire up audacity, and open the set. Make labels where you want to split the cd, under Tracks->Add Label at Selection.
Once you get all of these labels done, export them with File->Export Labels. Also make sure to export the project as a .wav file.
Use shntool to pad the wave file you are using - "shntool pad YOUR_WAV_FILE_NAME.wav"
Now we fix the cue sheet - Instead of the "BINARY" at the top, it needs to say "WAVE". Also make sure that the filename is the correct one - use the padded wav, not the unpadded one.
Now on to the burning. Insert a blank cd/dvd, and then use wodim to burn it with `wodim -dao cuefile="YOUR_CUE_SHEET.cue"`
If that all goes well, you will have a gapless cd! If nothing else, it worked for me.....

---

### Post by Chronon on 2010-03-25
Neat.  Thanks for sharing!

---

