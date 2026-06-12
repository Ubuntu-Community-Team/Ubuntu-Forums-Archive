---
title: "Record sound using alsa"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by akwatve on 2008-01-06
Hi

Is there any application (preferably with GUI) that will let me record sound using ALSA.
I tried audacity but no success (apparently it is designed for OSS...it just hangs when I try to record). krecord and krec are not meant for alsa and (as expected) they don't record anything when tried.
I tried command line alsa recorder

arecord -v -v -Dhw:0,0 -f cd test.wav

But no success. It creates a 17Kb file and crashes with following error message : 
"pcm_read:1346: read error : Input/Output error"
God knows what that means....

A related problem to this is skype not working on kubuntu... But I think if I can resolve the recording issue, it will be easier to make skype work.

I have an Acer Aspire 5052NWXMi laptop with AMD Turion 64X2

Thanks,

---

### Post by ron999 on 2008-01-06
Hi
I use arecord.
The instruction is:-
**arecord -f cd output.wav**

There's no GUI but I followed the instructions in this tutorial:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

---

### Post by akwatve on 2008-01-06
I tried it. It just creates a 44byte empty wave file. I have one in-built mic and another mic jack on the front panel. I am not sure which mic is it trying to use. In my mixer I have two capture columns(which I assume correspond to these two mics). I have checked both of them and they are set at 100% level.
I can hear my voice from the speakers but for some reason alsa is unable intercept and record it. :-(

Thanks anyways

---

### Post by akwatve on 2008-01-22
Can someone help me.... I have no success with recording :-(
This is giving me a headache

---

### Post by ron999 on 2008-01-22
Hi
arecord doesn't record from the mics. It just records whatever is coming through your sound channel at the time, which may be from the mic or music or whatever.
Please read the tutorial again in my link above.
This is the difficult bit, got to get it right:-
[B]First of all you have to set up the recording channels by doing

alsamixer

Once there, select the capture view by typing the tab key.

With the arrow keys select the column Capture and set it to the CAPTUR mode with the space key as in the screenshot. Adjust the recording volume with the arrow keys..[/B]

---

### Post by akwatve on 2008-01-23
Yup... I did exactly that.

I opened alsa mixer selecte "capture" option, and set the volume. But no success ... All i get is an empty wave file.
There is a option to select "Input Source" on the same screen. it allows us to select which input source to use for capture. In the hope of makeing things work i tried setting it to mic and front-mic but still could not get recording to work.....

---

### Post by akwatve on 2008-01-31
I just verified that alsa cannot record even from the external microphone. I got a headphone and plugged in its mic in the soundcard mic jack. Though I was able to hear myself from the speaker, Alsa just refused to record anything.
I am not sure why does this happen. I did follow every step in the tutorial suggested ron999.

---

### Post by erginemr on 2008-01-31
I have noticed the same; that I cannot record anything with ALSA. But I can record with my external mic using OSS. Did you try enabling the OSS as the source for recording from Gnome Main Menu -> Preferences -> Multimedia Systems Selector (or something similar)?

---

### Post by dabl on 2008-01-31
Not knowing anything more than what I read here, I'm going to suggest 2 things:

1. You really, really should use Audacity with alsa -- it is a bit "picky" about having exclusive access to your sound system, so you have to close other things that want to make noises, like your browser and music player, before you launch Audacity.  But it is a superior recording/playback/processing application for Linux.

2. Since I know nothing about your sound system, here's the guide to make sure you've got it configured optimally:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Hope this helps.  :)

---

### Post by akwatve on 2008-01-31
> **erginemr said:**
> I have noticed the same; that I cannot record anything with ALSA. But I can record with my external mic using OSS. Did you try enabling the OSS as the source for recording from Gnome Main Menu -> Preferences -> Multimedia Systems Selector (or something similar)?

By OSS did you mean OSS4 or Alsa-OSS emulation?  I have tried OSS4. Although it does record sound it doesn't play anything. I mean It plays but I cant hear anything from the speakers. Its output is directed to some device, I don't know about. I did file a bug-report about this with 4front technology but havent really got a concrete solution.

audacity is the only program I know of which can record from oss. Krec and krecord are utterly useless. But half of the times audacity cannot detect devices. When it does, it cannot open input device for recording (thats what the error message says) Further, whenever audacity cribs about device failures it almost certainly hangs. This also answers suggestion given by 'dabl'. So far my experience with audacity has been miserable. In fact failure to use audacity forced me to try command line recording :-)

Is there any program that can record sound using oss interface ?

Thanks guys for your help,
akwatve

---

