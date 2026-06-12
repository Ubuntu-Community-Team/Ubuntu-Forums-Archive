---
title: "Ripping audio from DVDs"
date: 2008-05-31
forum: Multimedia Software
---

### Post by aweller on 2008-05-31
Dear all,

I have several live DVDs that I would like to extract the audio from so I can listen to it on my personal music player.  I would like to do this track by track, not in one block.

I have relentlessly searched the forums, tried VLC, Acidrip, Avidemux, transcode (with problems), dvd::rip...  But so far I have been unsuccessful.

Is there an easy, quick way to get ogg audio from my DVDs?

Thanks, Andy

---

### Post by xc3RnbFO8P on 2008-05-31
I use DVD:RIP and then Avidemux.
Rip it to the harddisk
Open the first VOB with Avidemux
Avidemux ask you if you want to append the rest of VOBs, do so.
On the left bar Audio> choose the format and configure
On top bar choose Audio> save

---

### Post by aweller on 2008-06-22
Thanks for this.  It seems to do it as one block though.  Is it possible to do it track-by-track?!

For example, if I have a live DVD with 10 videos/tracks on, instead of having one ogg for all, I would like 10 oggs for each separate track.

Thanks!

---

### Post by mc4man on 2008-06-22
In cases where each track is a chapter I use mplayer to extract to .wav and then convert as needed
```
mplayer -vc null -vo null -aid 129 -ao pcm:fast:waveheader:file=stones1.wav dvd://2 -chapter 9-9
```
The -aid  which audio stream (listing shown when opening dvd in mplayer from cli)
file=  the name you wish of output file
dvd://2  - which title on dvd

In cases where the track is spread across chapters I use dvdshrink to reauthor a single title w/ 1 chapter using the start/stop feature and then extract

---

### Post by aweller on 2008-06-22
I was looking at transcode too from here: [www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html](www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html)

Based on a quick reading, I have adapted my code to this:

transcode -i /dev/dvd -x dvd -T 2,2 -a 0 -y null,ogg -b 128,0,4,0 -o Track1.ogg

It seems to work, however I am confused as to the bitrate.  Ideally I want an ogg quality level of 4 or 5.

How do I do that with transcode?

Thanks!

---

### Post by aweller on 2008-06-22
Thanks mc4man!

Can you clarify some things for me please.

I am not sure how to get the audio stream from the "listing shown when opening dvd in mplayer from cli"?!

The "-chapter 9-9" bit means just chapter 9, yes?!  i.e. from chapter 9 to chapter 9?!

Thanks!

---

### Post by mc4man on 2008-06-22
> The "-chapter 9-9" bit means just chapter 9, yes?! i.e. from chapter 9 to chapter 9?!
 Yes
As I remember a couple of svn versions i compiled in april the chapter comm. seemed broken, I went back and compiled the hardy repo source and it was fine
From transcode help
> -b b[,v[,q[,m]]]    audio encoder bitrate kBits/s[,vbr[,quality[,mode]]] [128,0,5,0]

> I am not sure how to get the audio stream from the "listing shown when opening dvd in mplayer from cli"?!


edit:
```
doug@doug-desktop:~$ gmplayer
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team 
........clipped
Playing dvd://1.
There are 9 titles on this DVD.
There are 21 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: zh aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.

```
In this case (Hero) aid 128 is chinese, aid 129 is english. probably on concert dvd they would all be one language, I'd probably use the closet one to stereo, ie. ac3 2.1 or a lpcm if present, no big deal really if you use the 5.1

---

### Post by aweller on 2008-06-23
Thanks for this.  I will give it a try later.

I did read the transcode help, but it doesn't make much sense to me?!?

Why can't you just do "-q4", for example, like you can with oggenc?!

So, with transcode, would I just do "-b b[q4]" to get my 'quality' value of 4?!

Thanks!

---

### Post by mc4man on 2008-06-23
> So, with transcode, would I just do "-b b[q4]" to get my 'quality' value of 4?!

I'm not the one to advise you on that, never used transcode.
On the face of it your orig. setting seems more appropriate.
 ogg -b 128,0,4,0
looks like bitrate - 128, vbr - off, quality - 4, mode - none (? on mode)

---

