---
title: "[SOLVED] Mass conversion of .wav to .ogg?"
date: 2008-07-18
forum: Multimedia Software
---

### Post by vbman11 on 2008-07-18
So here's my problem:
      I bought a bunch of stuff off the itunes music store. Then (after I started using ubuntu) I burnt it all(protected aac's) to cd's to import into Exaile. I copied the rest of my collection into my music directory. then I took the .wav's directly off the cd renamed them and put them into my music directory in the "correct" dirs ([artist]/[album]/[song].*) as the rest of the music. well now I want to convert all of them to .ogg so I can use ID3. I have already tried Sound Converter and it's kde equivilent Sound Konverter, but both gave wierd errors, so I moved on to ffmpeg, here is what I came up with:

ffmpeg -i /home/kevin/Music/*/*/*.wav /home/kevin/Music/*/*/*.ogg
Will this work?
I noticed, while playing with ffmpeg, I can set the ID3 tags just by adding a couple of args, can I use the dir names to set those?

Lastly, are there any WORKING programs to do this in a lot easier way?

---

### Post by logos34 on 2008-07-18
To convert wavs to ogg in the CLI I personally prefer to call the ogg codec directly:

man oggenc

> I noticed, while playing with ffmpeg, I can set the ID3 tags just by adding a couple of args, can I use the dir names to set those?

show us exactly what you want to change by posting an ID3 tag

---

### Post by ad_267 on 2008-07-18
What errors did you get with sound converter? Would be helpful if you actually specified, as it works fine for me and I'm sure many other people.

---

### Post by vbman11 on 2008-07-18
Ok, so the wav file doesn't support an ID so I wanted to add the title/album/artist to the ogg automatically. And I tried sound converter again and It does convert fine, but I only want to convert the .wav's to .ogg's. Can you do that in sound converter?



BTW this is the only thing keeping me using Itunes.

---

### Post by ad_267 on 2008-07-18
In SoundConverter click on Add Folder, click on the bar next to Filter and select .wav then select the folder. Easy peasy.

---

### Post by logos34 on 2008-07-18
Ok, I see what you're saying...If you're still getting errors in SoundConverter, try [dBpoweramp music convertor]("http://www.google.com/url?q=http://www.dbpoweramp.com/dmc.htm&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNHDMqPbwELJDkE2UMmF-PXtQrPr-w").  It's the best.  Then you can add artist/album/track there, pretty simple

---

### Post by vbman11 on 2008-07-18
Ok so I figured it out:

"$ soundconverter /home/kevin/Music/*/*/*.wav"

this loads only the wanted wav files and then I can convert them.

---

