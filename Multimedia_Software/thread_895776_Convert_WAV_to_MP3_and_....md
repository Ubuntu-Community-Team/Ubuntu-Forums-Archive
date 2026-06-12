---
title: "Convert WAV to MP3 and ..."
date: 2008-08-20
forum: Multimedia Software
---

### Post by croniksoft on 2008-08-20
Hello everyone, 


i have a big music Collection (85gib) in .wav format witch i would like convert to MP3,i know of some programs that can do this but what i really need is that after the conversion happen that the .wav file will get replace by the new .mp3 file,,,i want this because my music is well organize and it would be a pain to reorder all of them

tks,
Cronik

---

### Post by knightcoder on 2008-08-20
I think audacity would do the job if you can succeed to record from your sound card.
It works great in windows, but in Linux, I had lots of trouble recording from my sound card with decent quality. But if you manage to do so, it'll be a breeze converting wav to mp3

---

### Post by croniksoft on 2008-08-20
Converting it is not the issue,the issue is replacing the old file with the new one

ex:

/home/user/Music/bachanta/aventura/mix/el perdedor.wav
to
/home/user/Music/bachanta/aventura/mix/el perdedor.mp3

---

### Post by FakeOutdoorsman on 2008-08-20
A script would do this just fine, check out the one by unutbu here: [Bulk converting ogg to mp3]("http://ubuntuforums.org/showthread.php?p=5503430").  In ogg2mp3.py (or whatever you decide to name it), change the line:
```
if extension == '.ogg':
```
to
```
if extension == '.wav':
```

---

### Post by ajgreeny on 2008-08-20
I think **soundconverter** is just what you want.  It will put all the files you convert into their source folder if that is what you want and will even delete the original file, though that seems dangerous without listening to the output file first, if you ask me.

I don't know if sox will do it as well, I seem to remember that sox doesn't encode mp3s, but can decode them.  Have a look for that and see if it helps.

---

### Post by croniksoft on 2008-08-20
Thank you guys,i think i will give soundconverter a try but thanx for the Python program anyways

---

