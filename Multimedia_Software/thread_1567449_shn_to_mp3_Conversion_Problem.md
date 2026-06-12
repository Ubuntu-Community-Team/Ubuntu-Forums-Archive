---
title: "shn to mp3 Conversion Problem"
date: 2010-09-03
forum: Multimedia Software
---

### Post by wbrokow1 on 2010-09-03
```
walter@walter-desktop:/media/disk-1/Music/Rush/1978-11-20 - Every Soul a Battlefield/Disc 1$ pacpl -to mp3  "103 A Passage To Bangkok.shn"
Perl Audio Converter - 4.0.4

Converting:  [103 A Passage To Bangkok.shn] -> [mp3] decode failed with exit status: 256


Total files converted: 0, failed: 1
walter@walter-desktop:/media/disk-1/Music/Rush/1978-11-20 - Every Soul a Battlefield/Disc 1$ 

```

I keep getting this error.
I have searched for months and tried every utility.
pacpl shntool shn2mp3 audacity and on & on & on..............

Anyone know of a good utility for converting shn to mp3

Also I am not sure at all but I think the shn files might be corrupted.

I only think this because I can get them to play for few minutes on any player: Xbox,xine mplayer rythymbox etc. then they crap out.

Any help is appreciated.

---

### Post by mc4man on 2010-09-03
Obviously the wildcard is you may have corrupted files.

You could try soundkonverter which would work fine.

-A couple of points (i don't actually use sk that much, just what I've noticed
Sometimes when making changes in sk you need to then close and restart sk for them to take effect. (at least in gnome

For shn and in  possibly in general I'd choose the Output 'copy directory structure'
Settings -> configure soundkonverter -> backends is where you need to ck. for encoding/decoding support - for shn make sure shorten is in a /bin in path


Edit; maybe also try using shorten to extract a file to wav - see if it errors
shorten -x [COLOR="Blue"]infile[/COLOR].shn [COLOR="Blue"]outfile[/COLOR].wav

---

### Post by wbrokow1 on 2010-09-05
Yes, I think the files were corrupt. Luckily I was able to re-download them.
Thanks for your help.:p

---

