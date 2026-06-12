---
title: "Video converter?"
date: 2009-05-31
forum: Multimedia Software
---

### Post by carlosgs91 on 2009-05-31
.

---

### Post by WindPower on 2009-05-31
This is kind of self-advertising, but you could try [DamnVid]("http://code.google.com/p/damnvid/"), created by yours truly (me). it's cross-platform and comes bundled with a fresh build of ffmpeg, which you could install using apt-get if you don't feel like installing DamnVid (sudo apt-get install ffmpeg). Not sure if Ubuntu repo's ffmpeg build has mp4 support though.

---

### Post by Thelasko on 2009-05-31
It's not in the repositories, but I understand [handbrake]("http://handbrake.fr/?article=download") is quite good.

---

### Post by carlosgs91 on 2009-05-31
.

---

### Post by ajgreeny on 2009-05-31
Avidemux certainly will do the job pretty well, I know because I have used it in the past but as you say it does need all the correct codecs and lib files on the system.

Look a bit more carefully and get all the codecs that you can find by searching for them in apt-get or synaptic and I'm sure you will be able to do the job.  Without all the codecs I don't think anything will be able to do what you want, so you will have to get them somehow or other.

---

### Post by khelben1979 on 2009-05-31
I made a search on sourceforge.net and [here's the result]("http://sourceforge.net/search/?type_of_search=soft&words=video+converter").

Maybe you'll find something of interest there?

---

### Post by paul.gevers on 2009-06-01
> **carlosgs91 said:**
> What libraries and/or programs should I install? I'm on Ubuntu 9.04

You need to install the unstripped version of libavcodec which is for Jaunty: libavcodec-unstripped-52. It is in the multiverse repository (which most people use anyway).

---

### Post by bgiannes on 2009-06-01
follow this ffmpeg build

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

then install winff 
> sudo apt-get install winff

or (this is the best option)

learn to use ffmpeg from the command line

eg

Extracting sound from a video, and save it as Mp3
> ffmpeg -i source_video.avi -vn -ar 44100 -ac 2 -ab 192 -f mp3 sound.mp3


write mp4 to avi same Q
> 
ffmpeg -i "source video.mp4" -sameq -vcodec libxvid -acodec libmp3lame "outfile.avi"


make divx avi
> ffmpeg -i "source video.<mp4,avi,mov,etc>" -ab 256k -ar 48000 -b 1800k -vcodec libxvid -acodec libmp3lame "outfile.avi"


two pass good res vob to avi
> ffmpeg -y -i infile.vob -pass 1 -vcodec libxvid -b 512k -bt 512k -threads 0 -f avi -an /dev/null && ffmpeg -i infile.vob -pass 2 -acodec libfaac -ab 128k -ac 2 -vcodec libxvid -b 512k -bt 512k -threads 0 -f avi outfile.avi


vob batch to avi
> cat *.vob | ffmpeg -i - -ab 192k -ar 48000 -b 1800k -vcodec libxvid -acodec libmp3lame "name goes here.avi"


ipod encode, (i never tested this i only have a nano)
> ffmpeg -i source_video.avi input -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X final_video.mp4

---

### Post by FakeOutdoorsman on 2009-06-01
You need to enable restricted encoders in FFmpeg for WinFF to encode to mpeg4:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by slipdipper on 2009-09-18
i have to say, i just started using DamnVid, and its freakin awesome. i was having a ton of problems with converting a mkv to avi (sync issues), and it does it without breaking a sweat.. for whatever reason i couldnt get my ffmpeg syntax right, and every ffmpeg script, mencoder script and other tool couldnt fix my sync issues. this includes handbreak, avidemux and winFF. at the end of the day damnvid was a simple tool that had all the right ffmpeg presets to produce a reliable conversion every time. 

It also has a ton of modules and features for converting online videos. i dont have much of a need for that, but for all my VOB to AVI, MKV to AVI, and AVI to PSP conversions i'll be using this. Whats nice too is that you can ps auxw and see the ffmpeg command used which is helpful when learning how to use ffmpeg. also the preferences.damnvid is easy to modify so you can have any conversion types you want. conversion profiles are easy with conf.ini too. 

my biggest issue is that i have to go to the shell to edit preferences. the add profile feature doesnt work all that good (doesnt create a new profile to add, just allows you to create names)... and i cant add a new resolution without modifying the preferences page. finally i'd like to see a feature where i could merge VOBs, right now i have to do that manually. anyway.. damnvid, you rock.. you're my new best friend.

---

### Post by WindPower on 2009-09-19
> **slipdipper said:**
> i have to say, i just started using DamnVid, and its freakin awesome. i was having a ton of problems with converting a mkv to avi (sync issues), and it does it without breaking a sweat.. for whatever reason i couldnt get my ffmpeg syntax right, and every ffmpeg script, mencoder script and other tool couldnt fix my sync issues. this includes handbreak, avidemux and winFF. at the end of the day damnvid was a simple tool that had all the right ffmpeg presets to produce a reliable conversion every time. 

It also has a ton of modules and features for converting online videos. i dont have much of a need for that, but for all my VOB to AVI, MKV to AVI, and AVI to PSP conversions i'll be using this. Whats nice too is that you can ps auxw and see the ffmpeg command used which is helpful when learning how to use ffmpeg. also the preferences.damnvid is easy to modify so you can have any conversion types you want. conversion profiles are easy with conf.ini too. 

my biggest issue is that i have to go to the shell to edit preferences. the add profile feature doesnt work all that good (doesnt create a new profile to add, just allows you to create names)... and i cant add a new resolution without modifying the preferences page. finally i'd like to see a feature where i could merge VOBs, right now i have to do that manually. anyway.. damnvid, you rock.. you're my new best friend.
The add profile thingy is already fixed in the trunk but I don't advise building it from source; the building script requires some packages and all so it probably won't work anyway. I'd wait for the next release, which has localization :o

You can set your own resolution, just type it in the dropdown boxes. Some dropdown boxes contain a fixed set of options (like the audio codec), others are editable (those that are a dropdown box and a text box at the same time), so you can type whatever resolution you wish, like 300x100, I dunno, into the box, without editing the config files.
As for merging VOB's, I'm not sure how I'd "integrate" that into the interface :-k

And thanks for all the praise :)

---

### Post by Kyle.Gant on 2009-10-17
*bump* i also need a video converter...

i tried to DL Damnvid, but was unable. idk if there is something wrong with the source of if i am yet again experiencing a PEBKAC error, but i can't DL it. 

alternatively any suggestions to a good vid converter going from everything to avi? I'm trying to convert all of my movies to avi to save space and various other reasons...

*********************************NEVERMIND!!!*****************************
 i fixed my own problem (for once)

---

### Post by chelovek84 on 2010-10-07
[http://transcoder84.sourceforge.net/](http://transcoder84.sourceforge.net/)

---

