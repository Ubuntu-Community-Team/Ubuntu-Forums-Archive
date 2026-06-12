---
title: "Need good, simple to use, DAW program."
date: 2016-06-29
forum: Multimedia Software
---

### Post by Autodave on 2016-06-29
Audacity worked fine until I upgraded to 16.04. Now, I get a distortion every 2 minutes that lasts for 15 seconds. Even the Audacity forum has not been able to help. So, I am looking for new DAW program that is easy to setup and make work. I have played for hours with Ardour with very little luck. 

What I am looking for is to record 18 channels via USB cable. And then, I need to be able to edit out what I don't need. I do not need any special effects, or adding of tracks later. Simply record, edit, save, export as MP3 or WAV..

Any suggestions?

Thanks in advance.

---

### Post by gordintoronto on 2016-06-29
This might be a bit dated, but it might show you some options:
[http://www.techdrivein.com/2014/02/10-music-production-tools-for-ubuntu-linux.html](http://www.techdrivein.com/2014/02/10-music-production-tools-for-ubuntu-linux.html)

What was wrong with Ardour?

---

### Post by shantiq on 2016-06-30
you  can use command-line SoX

```
 sudo apt-get install sox libsox-fmt-all
```


then use

```
 rec -b 24   "name of track".flac  gain +20
```


to record
CTRL+c to stop


then go to Audacity to trim manipulate etc...


SoX is very stable at the recording stage Audacity not so


PS:   if 24-bit flac not your thing use any of those formats


> 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au avr awb caf cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 fap flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud mp2 mp3 nist ogg paf prc pvf raw s1 s16 s2 s24 s3 s32 s4 s8 sb sd2 sds sf sl sln smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox w64 wav wavpcm wv wve xa xi



---

### Post by Autodave on 2016-06-30
Thanks to both of you for replying. I have looked at and tried just about everything in that list and a few others with no luck at all.

As for the command line recording, that definitely is intriguing. I would sure love to have a GUI so that I could see what was going on, but I will definitely give it a try.

---

### Post by Autodave on 2016-06-30
Missed part of your reply: sorry.  I have played w/Ardour on 2 different machines and cannot get it to work at all. I believe it is probably the sound card, but not sure. All I get is loud hissing noise. So far, I have only tried it at home using a stereo input just to see if I can get it to work.  I need to make sure it will work before taking it to the church and actually recording with it. The only time I would get to record the 18 channels would be during a church service. I record the sermon during the first service using Audacity and the stereo outputs from the board. But, we are wanting to someday put the entire service on the website: that will require the 18 channels and some mixing and editing.

---

### Post by kazakore on 2016-06-30
Have you considered enabling the KXStudio repos and seeing if that updates Audacity to a version working correctly? Generally they are much better at keeping audio software uptodate and they are based around Ubuntu and many people use their repos on top of Ubuntu Studio with no issues (including myself.)

Other than that, if you don't like Ardour or Rosegarden the only other one from that list that may have features enough for you is LMMS. Not used it myself though...

---

### Post by Autodave on 2016-07-01
I am running the most current version of Audacity: I know that for sure. Audacity was the perfect DAW for me: simple to use: worked pretty much as soon as I installed it. Having never used a DAW before, I was quite please with what it could do and the ease of setup. Then Xubuntu 16.04 came along and I did a complete in stall (not an upgrade) and everything seemed fine until I listened to what I had recorded and found this weird static noise that lasted for about 15 seconds and then faded out only to return about 2 minutes later. This repeated the whole way through. Thinking that maybe the machine that I was using had met its limits (although TaskManager) said that nothing was being used anywhere near its max capabilities, I then used a new machine with much better specs, only to have the exact problem. I tried clean installs on both 32 and 64 bit systems: absolutely no difference. I changed all the presets for the quality of the recording: whether at best configuration or worst, same problem.

I even joined Audacity's forum and no one there can offer any assistance.

I don't have a problem changing to another program, but I have not been able to get any of them set up to even record 2 channel stereo! It is probably me, in fact I know it is me and my lack of DAW experience, but 8 hours last Saturday trying Ardour and LMMS gave me nothing but frustration.

---

### Post by Autodave on 2016-07-10
Got it fixed today: kinda. Reverted back to Xubuntu 14.04 and Audacity 2.0.5 and everything worked fine: 18 channels @ 44.1 kHz at high sampling rate via USB cable. No probs whatsoever.

---

