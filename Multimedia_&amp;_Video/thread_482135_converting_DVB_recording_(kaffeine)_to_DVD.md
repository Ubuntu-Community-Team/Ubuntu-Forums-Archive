---
title: "converting DVB recording (kaffeine) to DVD"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by paradoxni on 2007-06-23
In windows I converted such DVB recordings, by demuxing the stream to seperate audio and video files, then using mpeg2schmidt to cut out the commericals (this cut both video and audio files simultaneously) then i converted the files to DVD vob's.

In ubuntu ive managed to demux the stream using ProjectX and now have seperate m2v and mp2 files, but which program can I use to cut both files simultaneously?

I can add the video and external audio into avidemux, but according to [this wiki]("http://www.avidemux.org/admWiki/index.php?title=Cutting#External_audio_source") avidemux will not cut the external audio file

PS the reason I want to demux and cut is to help with audio sync issues.

---

### Post by mtron on 2007-06-27
The way i'm doing it:

1.Demux the recording with the Java app ProjectX (set Cutpoints ,Error Correction of the stream, ect)  You'll get  minimum one audio stream (filename.mp2) and video stream (filename.m2v)

2.Join the demuxed  audio & video streams with mplex  "mplex -f8 -o file.vob filename.m2v filename.mp2" again in one mpeg

3.With the help from the  console App dvdauthor (very fast) or with the  gui mandvd you can add DVD Menus ect, and produce the vob and fifo files

4. Burn them with gnomebaker or K3B.

Some alternative Video Cutters:

TTCut - [http://ttcut.tritime.de/startseite.2.html](http://ttcut.tritime.de/startseite.2.html)

DVBCut - [http://dvbcut.sourceforge.net](http://dvbcut.sourceforge.net)

GOPDIT - [http://gopdit.ath.cx/](http://gopdit.ath.cx/)

GOPchop - [http://gopchop.sourceforge.net/index.php](http://gopchop.sourceforge.net/index.php)


Pick the one you like!

---

### Post by paradoxni on 2007-06-27
thanks for the reply... I actually did it in the end, quite a similar way to you but using different programs

1. PROJECTX to demux
2. AVIDEMUX to remux the video/audio + cut out sections i do not want, converting to a DVD compliant mpeg2 stream in the process.
3. DEVEDE to create the vobs, with the option "video is already DVD compliant", so no conversion is needed.
4. K3B to burn.

---

### Post by xfile087 on 2007-06-27
> **paradoxni said:**
> thanks for the reply... I actually did it in the end, quite a similar way to you but using different programs

1. PROJECTX to demux
2. AVIDEMUX to remux the video/audio + cut out sections i do not want, converting to a DVD compliant mpeg2 stream in the process.
3. DEVEDE to create the vobs, with the option "video is already DVD compliant", so no conversion is needed.
4. K3B to burn.

I've just bought a TV card and got it working with Ubuntu and just wanted to say thanks for posting back how you managed to cut/burn to dvd. I will find that very useful in the future!

---

### Post by paradoxni on 2007-06-27
well if you have any trouble, post back and we will try to help (althou im no expert :) )

---

### Post by xfile087 on 2007-06-27
> **paradoxni said:**
> well if you have any trouble, post back and we will try to help (althou im no expert :) )

Actually I do have one question if you don't mind. Recordings done with Kaffeine? Do they play okay? For instance I just recorded a 2 hour film so I can watch later, but unless I play with Kaffeine then other players like VLC think its 22 hours long so I can't fast forward etc. Just wondering if it was just me?

---

### Post by paradoxni on 2007-06-27
just tried a test recording there and it plays fine in all players with fast forward etc. so i dont know?! what format are you recording to ?

---

### Post by xfile087 on 2007-06-27
> **paradoxni said:**
> just tried a test recording there and it plays fine in all players with fast forward etc. so i dont know?! what format are you recording to ?

I haven't changed any settings so it will be the default format. Did you change yours?

---

### Post by paradoxni on 2007-06-27
cannot remember , but its set to TS

---

### Post by xfile087 on 2007-06-27
> **paradoxni said:**
> cannot remember , but its set to TS

Okay, thanks. I'll look into it

---

