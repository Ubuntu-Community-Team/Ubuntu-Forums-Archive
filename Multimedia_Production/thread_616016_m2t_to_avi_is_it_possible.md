---
title: "m2t to avi: is it possible?"
date: 2007-11-17
forum: Multimedia Production
---

### Post by fermo111 on 2007-11-17
I have a DVB-T card and use Kaffeine for TV recording. Kaffeine saves recordings in .m2t files, which, I believe are in MPEG-TS format.

I can replay them using Kaffeine, but I haven't been able till now to convert them into AVI. Whatever method I try, I always get an AVI with audio out of sync.

Any help is very appreciated.

Luca

---

### Post by yabbadabbadont on 2007-11-17
I found a lot of information on how to do it using windows software, but not much with native software.  Maybe reading through the following will give you some ideas:

[http://forum.videohelp.com/topic303573.html](http://forum.videohelp.com/topic303573.html)

---

### Post by Creative2 on 2007-11-18
mmm 
i think you can easly 

force syncro and convert

mencoder -idx  INPUT -ovc copy -oac copy -forceidx -o OUTPUT
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=720:576 -xvidencopts fixed_quant=4 -o OUTPUT. avi

or ntsc format :

mencoder -idx INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=720:480 -xvidencopts fixed_quant=4 -o OUTPUT. avi

you can try replacing -idx with -forceidx or after conversion with 
 

mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT

---

### Post by fermo111 on 2007-11-18
Thanks to Creative2 and yabbadabbadont for your answers.

Using mencoder as suggested by Creative2 seems to work quite well.

I would also like to know what would you suggest I'd use to edit the recording to cut commercials and the last part of it (say when i record past the end of the show).

Thanks a lot

Luca

---

### Post by regomodo on 2007-11-18
is there any easier way of doing this? i would look into using mencoder but it's rather urgent

[nvm] there is decent freeware in windows for this. can't find anything in linux. cinelerra, kino, kdenlive, avidemux. They are all pretty useless. Nothing in linux touches dgindex with virtualdubmod  and mpeg-streamclip unfortunately.

---

### Post by Creative2 on 2007-11-19
well if you want cut an avi you can use ( before you must install transcode... sudo apt-get install transcode)

avisplit -i INPUT -o OUTPUT -t { Choose the time range example: 00:10:00-00:11:00}
so for example wil be

avisplit -i INPUT -o OUTPUT -t: 00:10:00-00:11:00

if you have many avi you can merge
with 

avimerge -o  bigfile.avi -i  /path/inputfile1.avi /path/inputfile2.avi

we are developing convertIT to do someworks 

see here 
[http://it.youtube.com/watch?v=JSPuGnFPMdk](http://it.youtube.com/watch?v=JSPuGnFPMdk)

if youi are interested you can find information here 
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by regomodo on 2007-11-19
cheers creative2. I'll check that later.

I found [this]("http://www.squared5.com/") and the beta version is awesome. It is so bloody simple to use and doesn't require installation.

Unfortunately it's mac or windows and doesn't seem to make good use of my processor. It barely uses it.

I may give it a bash in wine but i doubt it'll work.

---

### Post by Smark on 2008-01-03
it is better to edit the m2t files using [ProjectX]("http://students.washington.edu/cdobrich/ProjectX_0.90.4.zip") (nice piece of software written in java) and then convert in the format you like :popcorn:

---

### Post by eye208 on 2008-01-04
> **regomodo said:**
> I found [this]("http://www.squared5.com/") and the beta version is awesome.
Looks like [Avidemux](http://en.wikipedia.org/wiki/Avidemux) to me. Avidemux is in the Ubuntu repos too. You may want to give it a shot.

---

### Post by Pigeon. on 2008-01-23
> **Creative2 said:**
> mmm 
i think you can easly 

force syncro and convert

mencoder -idx  INPUT -ovc copy -oac copy -forceidx -o OUTPUT
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=720:576 -xvidencopts fixed_quant=4 -o OUTPUT. avi

or ntsc format :

mencoder -idx INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale=720:480 -xvidencopts fixed_quant=4 -o OUTPUT. avi

you can try replacing -idx with -forceidx or after conversion with 
 

mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT

Got the same problem myself, but none of these methods work, they still produce an avi with sound out of sync. mplayer manages to play the raw .m2t with sound in sync, but not the avi. Also mencoder segfaults after it's transcoded about 1.7 gigs of the .m2t, which is less than half of it.

---

### Post by Creative2 on 2008-01-23
audio delay

```
mencoder -oac copy -ovc copy -audio-delay 05.000  INPUT -o OUTPUT
```

Fuoco tools has all this command line...in eXtRa...se here 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=652843](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=652843)
if you want use terminal 

this  Encode only a part of the movie so you can test if audio delay works fine or not ...you must replace hh:mm:ss etc ....with your prefered time...
```
mencoder INPUT -oac copy -ovc copy -audio-delay 05.000  -ss  hh:mm:ss.ms  -endpos hh:mm:ss.ms  -o OUTPUT
```

---

### Post by eye208 on 2008-01-23
> **Pigeon. said:**
> none of these methods work, they still produce an avi with sound out of sync.
Let's face it: AVI sucks. It cannot handle B-frames, it cannot handle variable framerate video, it cannot handle variable bitrate audio. It sucks because it's OLD!

Here's how to make a Quicktime-compatible MPEG-4 file:

mencoder INPUTFILE -vf scale=[COLOR="Red"]__[/COLOR]:[COLOR="Red"]__[/COLOR],harddup -ovc x264 -x264encopts bframes=1:no8x8dct:bitrate=[COLOR="Red"]__[/COLOR]:pass=1 -oac faac -faacopts object=2 -mc 0 -noskip -of rawaudio -o audio.aac
mencoder INPUTFILE -vf scale=[COLOR="Red"]__[/COLOR]:[COLOR="Red"]__[/COLOR],harddup -ovc x264 -x264encopts bframes=1:no8x8dct:bitrate=[COLOR="Red"]__[/COLOR]:pass=2 -nosound -mc 0 -noskip -of rawvideo -o video.h264
MP4Box OUTPUTFILE.mp4 -new -fps [COLOR="Red"]__[/COLOR] -add audio.aac -add video.h264

MP4Box is part of the GPAC suite (sudo apt-get install gpac).

---

### Post by zatoichi0 on 2008-01-29
I had a sync issue while trying to convert rvmb (RealMedia) to avi (xvid). The only thing that gave synced a/v was:
  
[INDENT]      -oac pcm[/INDENT]

Trying to recode with any compression broke a/v sync until I used **constant** bitrate, e.g:

[INDENT]mencoder ... -oac mp3lame -lameopts cbr:br=192 ....[/INDENT]

The harddrop option was also needed.

Hope this is useful for somebody...

---

### Post by kiikkuja on 2008-03-24
I have really tried using the avidemux 2 in ubuntu but all i get is video files with audio out of sync. 

The audio seems to be out of sync from the start and it seems to me that
i cannot fix it with shift function no matter in which direction I shift the audio damnit! 

I tried the mencoder code provided here and atleast the audio is in sync with the video.

I have alot of m2t files recorded with dvb and i want to cut the commercials and basically everything useless from them.

What tools would you recommend using to get ~700/350mb video files with audio in sync with the video @best video quality possible.

Pretty Please!!

---

### Post by kiikkuja on 2008-03-25
Bump! Anyone?

---

### Post by r76 on 2008-04-19
> **Smark said:**
> it is better to edit the m2t files using [ProjectX]("http://students.washington.edu/cdobrich/ProjectX_0.90.4.zip") (nice piece of software written in java) and then convert in the format you like :popcorn:

This answer seems to have been overlooked - use ProjectX (good guide and binary on doom9.org - remember the binary is java so just as good on linux as windows).  I then remux using mplex (in the package mjpegtools) and open the .mpg with avidemux which makes trimming out ads etc, saving as .avi / .mp4 / or just .mpg for easy dvd mastering a piece of cake.

Also I think Kaffeine can save as .ps (which is just mpeg2 anyway) can't it?  I don't bother because i like to check the error log of ProjectX.

---

