---
title: "[SOLVED] DivX, Xvid, Avi, x.264, h.263 Which is compatible with ...?"
date: 2007-09-26
forum: Multimedia Production
---

### Post by Amazona aestiva on 2007-09-26
Hi!
I'd like to know which format is fully compatible with "DivX Certified" DVD Players.

My experience:
Quite lot of the DivX files are incompatible
Same with XviD
I can't play h.263 and x.264 files at all!

I've tried 3 "DivX Certified" player.

However under Windows or Linux I can play my files very well.

What should I do?

---

### Post by chrome307 on 2007-09-26
Only DivX and Xvid - not H264, x264, mkv etc

Also you have to bear in mind that standalone players are based on 2 chipsets SIGMA and ESS .... you can recode to either one for playback in your device

AutoGK (Windows) allows you to choose which chipset for encoding purposes for playback in your device.
 
Plus your standard Mpeg2, Mp3 etc

**Grab yourself a DivX Test CD **

[http://divxtest.surdvd.com/sommaire.php3?lang=en](http://divxtest.surdvd.com/sommaire.php3?lang=en)

also on that site you will find reviews of players

---

### Post by Amazona aestiva on 2007-09-27
> **chrome307 said:**
> Only DivX and Xvid - not H264, x264, mkv etc

Also you have to bear in mind that standalone players are based on 2 chipsets SIGMA and ESS .... you can recode to either one for playback in your device

AutoGK (Windows) allows you to choose which chipset for encoding purposes for playback in your device.
 
Plus your standard Mpeg2, Mp3 etc

**Grab yourself a DivX Test CD **

[http://divxtest.surdvd.com/sommaire.php3?lang=en](http://divxtest.surdvd.com/sommaire.php3?lang=en)

also on that site you will find reviews of players

Thanks I'll download a CD!:)

---

### Post by Amazona aestiva on 2007-09-28
The player doesn't play about 10 of the files on the CD.
I think I'll connect my computer and the TV together. Then I'll be able to watch everything that I want.

---

### Post by Creative2 on 2007-10-08
-first you must know if you use pal or ntsc for your Tv\dvd player then the only things you must set is the size of movie for  PAL  is  720:576  for NTSC is   720:480
cideo codec to use is xvid and mp3 for audio A[B]ND THE OUTPUT FORMAT CAN BE AVI
[/B]
-h264 is stil in developing so none dvd player can play a movie with this codec 
-mencoder can use divx 5 i think i have read something but...if i must encode i prefer xvid 

- if you want a nice dvd player and recoder buy KISS player ( :D it play ogg format hehe and it's the best on the world for dvd-divx playing...but it's NOT CHIP)

here you can find a nice table fo divx player 

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html)

i have used this mine commandline to see my video on my pioneer 440
[b]
PAL[/b] _;D it works K3B TESTED ON PLAYER\RECORDER PIONEER 440 H-S_

[b] [i]
PAL best quality\compression[/i] [/b]     for this format  the max size  to be playable must be 720:576;

but if the movie is not a multiple of 720:576 and you resize it to 720:576 it will be distorted (the command for mecoder is this :-vf scale=720:576)

so i suggest to use this: -vf scale -zoom -xy \720 
in this way you will respect the aspect ratio  

```
 mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=720:576 -xvidencopts fixed_quant=4 -o OUTPUT. avi 

```

***PAL medium***

```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale=720:576 -xvidencopts bitrate=600 -o OUTPUT. avi
```

[b]
PAL low[/b]
```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=92 -srate 48000 -vf scale=720:576 -xvidencopts bitrate=400 -o OUTPUT. avi 
```

**NTSC**  i don t know if it works i use pal :D !for this format  the max size  to be playable must be 720:480;

but if the movie is not a multiple of 720:480 and you resize it to 720:480 it will be distorted (the command for mecoder is this :-vf scale=720:480)

so i suggest to use this: -vf scale -zoom -xy \720 
in this way you will respect the aspect ratio  

**NTSC BEST quality\compression**
```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=720:480 -xvidencopts fixed_quant=4 -o OUTPUT. avi
```

**NTSC MEDIUM**
```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale=720:480 -xvidencopts bitrate=600 -o OUTPUT. avi
```
[b]
NTSC LOW[/b]

```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=92 -srate 48000 -vf scale=720:480 -xvidencopts bitrate=400 -o OUTPUT. avi
```
[b]

HDTV TRY THIS i dont know if it works i have not hd tv..[/b]

```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=1280:720 -xvidencopts bitrate=4000 -o OUTPUT. avi
```

---

### Post by Amazona aestiva on 2007-10-08
> **Creative2 said:**
> -first you must know if you use pal or ntsc for your Tv\dvd player then the only things you must set is the size of movie for  PAL  is  720:576  for NTSC is   720:480
cideo codec to use is xvid and mp3 for audio A[B]ND THE OUTPUT FORMAT CAN BE AVI

......

HDTV TRY THIS i dont know if it works i have not hd tv..[/b]

```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=92 -srate 48000 --vf scale=1280:720 -xvidencopts bitrate=4000 -o OUTPUT. avi
```

Alright I'll try these soon.
Thanks.

PS: I've used mostly AC3. Perhaps this is the problem.

---

### Post by Amazona aestiva on 2007-10-08
> **Creative2 said:**
> -first you must know if you use pal or ntsc for your Tv\dvd player then the only things you must set is the size of movie for  PAL  is  720:576  for NTSC is   720:480
cideo codec to use is xvid and mp3 for audio A[B]ND THE OUTPUT FORMAT CAN BE AVI

......

HDTV TRY THIS i dont know if it works i have not hd tv..[/b]

```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=92 -srate 48000 --vf scale=1280:720 -xvidencopts bitrate=4000 -o OUTPUT. avi
```


Hey! You were right! My DVD player doesn't like AC3!

Thanks again.

PS: I'll use your M.C.;)

---

### Post by Creative2 on 2007-10-09
damn i have seen an error -.-

:
--vf scale=1280:720 

correct:
-vf scale=1280:720 

so :

```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=1280:720 -xvidencopts bitrate=4000 -o OUTPUT. avi
```

---

