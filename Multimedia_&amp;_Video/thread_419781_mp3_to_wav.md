---
title: "mp3 to wav"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by jgengler on 2007-04-23
Hi!

I would like very much if somebody can suggest a good mp3 to wav converter for gubuntu edgy. 

Thanks a lot for any help,

Joe

---

### Post by bswilson on 2007-04-23
If you're looking for a command line tool that you can use in a script, then try [soundconverter]("http://freshmeat.net/projects/soundconverter/").  Otherwise, why not try [Audacity]("http://audacity.sourceforge.net/")?

---

### Post by heimo on 2007-04-23
Yeah, audacity should be able to do it. Personally, I'd probably use ffmpeg. At simplest:
```
ffmpeg -i file.mp3 file.wav
```

---

### Post by jgengler on 2007-04-23
Hi!

I would prefer a good gui program, not a command line program. Audacity is good but it is unable to convert all the mp3 files in a given directory one by one. It opens one window for each file, and the conversion should be done manually for each file, which is very tedious.

Are there any other options?

Thanks a lot for any help,

Joe

---

### Post by jgengler on 2007-04-24
Hi!

For me, soundconverter worked perfectly. In spite the fact it is a command line program, it has a very useful graphical interface. The only problem is that I should set the preferences from ogg to wav in the output file type every time I run it. But that's no problem.

Thanks a lot for this help,


Joe

---

