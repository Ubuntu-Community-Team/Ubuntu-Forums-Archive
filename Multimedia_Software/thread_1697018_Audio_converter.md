---
title: "Audio converter"
date: 2011-02-28
forum: Multimedia Software
---

### Post by carvalho2707 on 2011-02-28
hey,

i have a little problem and i think that someone here can solve it..
my Multimedia WD can't play DTS sound.. but in windows we have a program called AudioConverter that like the name convert DTS to AC3.. Anyone knows something in ubuntu that can convert the audio track ?

i hope so :)

---

### Post by ron999 on 2011-02-28
Hi
**ffmpeg** will probably convert these dts tracks.
Try a command like this:-
```
ffmpeg -i [COLOR="Red"]*filename*[/COLOR].dts -acodec ac3 -ab 192k output.ac3

```
If it works ok then you can use an ffmpeg GUI such as **WinFF**.

From here:-
[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by carvalho2707 on 2011-02-28
and the new song ttype wil have the max quality possible?

---

### Post by aeiah on 2011-02-28
> **carvalho2707 said:**
> and the new song ttype wil have the max quality possible?

not with the above command, no, it'll have an audio bitrate of 192k

someone [here]("http://forums.macrumors.com/showthread.php?t=547083") suggests ```
ffmpeg -i sample.dts -vn -threads 8 -acodec ac3 -ac 6 -f ac3 -ab 640k sample.ac3
```

which'll ensure its 6 channel (5.1) at 640k. i suppose it all depends on what your DTS bitrate is. as with all encoding, you may lose some quality but if it's done right you wont notice. with something as high quality as DTS and ac3 the chances are your hearing or equipment will be worse than the quality of the track


once you have settings you like, you can add it to a script or batch process a load of tracks on the command line quite easily

---

### Post by carvalho2707 on 2011-02-28
doesn’t Work

---

### Post by aeiah on 2011-02-28
> **carvalho2707 said:**
> doesn’t Work

thankfully im psychic, so ill be able to tell exactly what's wrong without you needing to provide any information what so ever.

---

### Post by andrew.46 on 2011-02-28
> **carvalho2707 said:**
> doesn’t Work

If you are using FFmpeg could you provide both the command you have used and the full, uncut terminal output?

---

