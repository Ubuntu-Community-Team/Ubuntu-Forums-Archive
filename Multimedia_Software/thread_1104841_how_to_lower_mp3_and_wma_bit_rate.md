---
title: "how to lower mp3 and wma bit rate?"
date: 2009-03-24
forum: Multimedia Software
---

### Post by gackt on 2009-03-24
Hi i just bought sansa fuze, and it only support limited bit rate, so how do i lower the wma (and other format) bit rate? i have wma music with bit rate around 1000kbps (cannot remember the exact rate) and i wont to convert it to say 320kbps. Thanks

---

### Post by Agent.Logic_ on 2009-03-24
I don't know about wma bitrates, but for re-encoding mp3 bitrates, see [this thread](http://ubuntuforums.org/showthread.php?t=537208). Hope it helps.

**EDIT**: Also, please note... converting the LAME way has an annoying bug. If your mp3 files happen to have an id3v2.x tag, it gets deleted after conversion. You might want to try a program called [dBpoweramp](http://www.dbpoweramp.com/dmc.htm), which has an excellent GUI, a range of options and also wma re-encoding support. It works well under WINE. And it does not have the above id3v2 tag bug either. But all of it comes with a price (literally!).

---

### Post by mc4man on 2009-03-24
If your wma is "around 1000kbps" then it's probably wma lossless.
In that case your best bet is to convert to .wav with mplayer and then whatever you want.
You could go back to wma2 though I'd probably use lame to do mp3's

If your sansa wants tags then it would be simple to do the complete conv. at once with a simple script (wma -> .wav -> .mp3 with tags (or without if not needed

Anyway a basic wma lossless to .wav batch convert command keeping the same track names would be this (at directory prompt where .wma's are

```
for f in *.wma; do mplayer "$f" -ao pcm:fast:waveheader:file="${f%.wma}.wav"; done


```

You can alter the output path by adding directly in front of "${f%.wma}.wav"

Simple example (make a dir. named temp, output there
```
mkdir temp && for f in *.wma; do mplayer "$f" -ao pcm:fast:waveheader:file=./temp/"${f%.wma}.wav"; done 
```

A script would be better for an all in one conv., if you want to do mp3's with or without tags let me know, atm I have it set to do 6, album, arist, trackname, track position, genre and year (wma's must be numbered for track position tag, ie. 01-, 02- , ect. (with or without the - as long as consistent

Edit: it's possible soundkonverter could handle wma lossless, you'd have to try

---

### Post by gackt on 2009-03-24
Thank Agent logic and Mc4man

@mc4man
i dont quite understand, if i suppose to enter this

mkdir temp && for f in *.wma; do mplayer "$f" -ao pcm:fast:waveheader:file=./temp/"${f%.wma}.wav"; done

then where my original wma file should be located? Should i state something in the syntax referring my wma files? Coz if this recursively search the hard drive then it will be a problem to me because i just want to convert some files.

Thanks

---

### Post by cubeist on 2009-03-24
> **gackt said:**
> Thank Agent logic and Mc4man

@mc4man
i dont quite understand, if i suppose to enter this

mkdir temp && for f in *.wma; do mplayer "$f" -ao pcm:fast:waveheader:file=./temp/"${f%.wma}.wav"; done

then where my original wma file should be located? Should i state something in the syntax referring my wma files? Coz if this recursively search the hard drive then it will be a problem to me because i just want to convert some files.

Thanks

Before running that command from mc4man, you will need to navigate to the directory where your .wav files are.  So, open a new terminal, then using the **cd** command you can navigate to the correct location.  So for example, if your .wav's are in a folder called downloads, you would type ```
cd ~/Downloads
```
(the ~/ characters will automatically fill in the first part of the directory name, usually */home/username*)
when you have changed into a directory, the prompt in the terminal will show the directory you are currently in.  You can also type **ls** at any time to see a listing of your files and folders...if you see your .wav's you are in the right place.

---

### Post by gackt on 2009-03-24
Sweet....Thanks!

---

