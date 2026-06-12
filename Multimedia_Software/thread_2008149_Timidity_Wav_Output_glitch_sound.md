---
title: "Timidity Wav Output glitch sound"
date: 2012-06-22
forum: Multimedia Software
---

### Post by theLured on 2012-06-22
Hello, when I convert a midi file to wav with Timidity, it gives me a crackling sound at the beginning. Fluidsynth doesn't seem to do this.

```
$ timidity -c /etc/timidity/fluidr3_gm.cfg -Ow C.mid

$ fluidsynth -l -i -a file -z 2048 /usr/share/sounds/sf2/FluidR3_GM.sf2 C.mid
```

I've tried timidity with it's default soundfont and the fluidR3_GM soundfont.

[Here's the wav file - http://www.sendspace.com/file/afv8hi]("http://www.sendspace.com/file/afv8hi")

I want to use timidity because it's faster and I have a LOT of midi files to convert.

Does anyone know why fluidsynth is so slow? it takes about 2-3 seconds to convert that single note midi file, while timidity has done it in a millisecond.

---

### Post by shantiq on 2012-06-22
i use this syntax with timidity   see if you get a different result?    






```
**timidity  filename.mid -Ow -o filename.wav**
```


or for higher quality


```
timidity --output-24bit -A120 filename.mid -Ow -o filename.wav
```


and for bulk

```
for f in *.mid; do timidity  "$f" -Ow -o  "${f%.mid}.wav"; done
```

or higher quality


> for f in *.mid; do timidity --output-24bit -A120 "$f" -Ow -o  "${f%.mid}.wav"; done




**ps** is your crackling sound in all players?

---

### Post by theLured on 2012-06-23
Thank you!

This command has removed the glitch sound.
```
timidity --output-24bit -A120 filename.mid -Ow -o filename.wav
```

The glitch sound was part of the file, you could even see it in audacity.

Thanks for the batch job. I'm using a python script to do the batch conversion.

I can hear that this timidity output is much better quality and it sounds more like fluidsynths output, the tone is fuller.
Yaaay.

---

