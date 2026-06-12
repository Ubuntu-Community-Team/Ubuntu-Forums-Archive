---
title: "wma VOICE codec support"
date: 2007-11-21
forum: Multimedia Production
---

### Post by Dave_Man on 2007-11-21
Hi, 

I administer the Linux stations on my faculty (Computer science) and I'm trying to set it up so that students will be able to watch streaming wma video lectures that my university provides.

I can watch the videos with no problem on all lectures but I'm having problems with the audio of some specific lectures.
I can hear all lectures encoded in wma1, wma2 etc.. but the only video lectures I can't hear are the ones recorded with wma VOICE.

Is there a specific codec that I need to add that will get this to work?

I'm using VLC to play the videos with the --rtsp-tcp flag.
The videos are using the MMS extension but I used a greasemonkey script to rename the links to RTSP ones.

Everything works great other than the audio on the lectures encoded with wma voice.
I tried googling it and everything I got was about wma, nothing specific to wma voice.

Anybody can help me?

Thanks.
Dave.

---

### Post by Master Siege on 2007-11-27
I am having a similar issue. 
I cannot listen to a wma-VOICE stream.
The address is mms://69.46.29.2/Station2
It is a radio show on from 9pm EST to 10pm EST.
It's a talk radio show relating to Mixed Martial Arts. [www.mmaweekly.com](www.mmaweekly.com)

I'd like to listen to it in Ubuntu instead of booting into windows.
This is the only thing I need windows for currently.
If there is a plug-in for this I'd be totally away from windows!!

Hope someone can help us out or point us in the right direction.

Does anyone know of a web player that would play these?
I know BBC news has a player on their site.  I heard they use wma-VOICE on some of their shows.

Thanks in advance.

---

### Post by NTolerance on 2007-11-28
Seems like the answer for voice codecs in general is mplayer + w32codecs.  totem-xine plus all the codecs in the repos is lucky to play compressed voice files at all, and even if it does playback skips and sounds very poor.  I have found that mplayer + w32codecs works well for WMA voice and for DSPGroup Truespeech WAVs.

---

