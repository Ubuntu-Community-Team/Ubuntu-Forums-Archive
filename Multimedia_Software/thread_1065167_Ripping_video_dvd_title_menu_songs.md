---
title: "Ripping video dvd title menu songs"
date: 2009-02-09
forum: Multimedia Software
---

### Post by hakcayurek on 2009-02-09
I watched Madagascar 2 yesterday. It is one of the best movies of the year (in my opinion, far better than the original). Hans Zimmer's songs are exceptional. Especially "Alex on the spot". They used the orchestral version of the song  in the  DVD Title Menu too.  I think it is great as a ringtone, so I want to capture the orchestral version from the DVD menu. 

I tried several ripping software (Thoggen, AcidRip, etc). All of them shows the tracks, but none of the tracks contain the menu and music I'm looking for. I thought DVD title menu have their songs on the DVDs. 

I also tried looking VOB files (assuming they contain not only tracks but also songs) but the default mounted version gave CRC errors (I guess I have to give some mounting options to mount video DVD correctly).

Is there a software that lets me save the songs from video dvd? Or some alternative software that would help me capture the audio to dsp? For example, xine shows the dvd menu correctly and plays the sound. Is it possible to use an intermediate program to capture DSP?

Thanks in advance.

---

### Post by mc4man on 2009-02-09
It's not that hard, though I'm not familiar with linux apps in this regard. (demuxing main menu audio

the dvd menu is not a title, it's usually to be found in the VTS_0[COLOR="Red"]X[/COLOR]_0.Vob of the main movie title.

So for instance if the main movie is title 1 you want VTS_01_0.Vob

While menu .VOB's may not be encrypted you'll still want to rip the .VOB vs. just copying. (you only need the rip that .VOB or stop after it's ripped



Then you'll just need to demux to usually a 2ch .ac3 and leave as is or convert that to what you wish. (for a ringtone you'd obviously need to convert

If you can't find a linux app (maybe avidemux ?), I can show you how to use DGIndex (dgmpgdec)

screen shows output from 'Hero' main menu after DGIndex processing


Edit: you can, if need be, change the extension of the .VOB to .mpeg, shouldn't usually affect the demux

---

### Post by hakcayurek on 2009-02-11
Thanks mc4man,

You were right. The DVD menus were one of the VOB files (all of them were in one file). I just copied that file with k9copy and planning to get the sound next. But the hard part is done :)

---

