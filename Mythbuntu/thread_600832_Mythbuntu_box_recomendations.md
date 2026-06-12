---
title: "Mythbuntu box recomendations"
date: 2007-11-02
forum: Mythbuntu
---

### Post by Angel700 on 2007-11-02
I want to make a DVR from a box I have, here are the specs:

2.4 ghz Celeron
1 gb ram
Nvidia Geforce FX 5500
160 GB hdd

I want to use this to watch live digital, and analog content, as well as record/rewind and all that other fun stuff.  I was wondering if it would be possible to use this as an HD DVR or would it not be worth it.  It would also help if I can get some recommendations on a tuner that I could use for both analog and digital content that would be best for my processor, I really want it to be a dual tuner.  Any help would be much appreciated.  Thanks!!

---

### Post by tgm4883 on 2007-11-02
You might be able to.  Take a look at this [http://ubuntuforums.org/showthread.php?t=570204](http://ubuntuforums.org/showthread.php?t=570204)

It may help.

Getting HD on a 2.4 celeron doesn't seem very likely (for playback, recording is easier and you can do that)

---

### Post by Meph1st0 on 2007-11-02
Angel700,

I run a P4 2.4 ghz processor with 1GB of ram with an Nvidia 6200 graphics card.  So it's pretty similar to yours. 

I am able to watch HD with this box.  I can even watch a recording while the tuner is recording another show.  What makes the biggest difference for this computer is (so far as I can tell) is that I have Xvmc enabled in the playback section of Mythtv's frontend setup.  I've been relatively happy with this box so far.

For my tuner I use a pcHDTV HD-5500.  I use it purely for HD but from what I've read it can also be used for standard def tv as well.  One drawback to this card is that you're stuck with a linux based distro.  I couldn't just switch to windows mce if I wanted to.  

I would not expect this computer to be able to handle two tuners.  As mentioned in the Mythtv wiki somewhere it's recommended an extra 1ghz of processing power for any additional tuner cards.  I may be wrong in that regard though.

Also, with a 160 GB hard drive, it's going to fill up pretty quick.  You can anticipate about 7.5 GB per 1 hour of HD recording.  It fills up quick.  There is a way to transcode recordings so that they take up less space on your hard drive but I have not put this feature to the test on my machine.

---

### Post by Angel700 on 2007-11-04
Thanks for the response guys!

@Meph1st0
From what I understand a P4 is a lot better than a celeron so I don't think its a good comparison. I was looking into that tuner you mentioned and I noticed that it does not have hardware encoding for the analog signal, will that be necessary for my system?  Thanks for the suggestions. 

@tgm4883
Do you mean it wouldn't handle HD at all or just live playback.  If the file is already recorded will it be fine?

Does anyone have any experience with a celeron and HD?

---

### Post by newlinux on 2007-11-05
I can't speak directly to the celeron, but like meph1st0 I have a P4 (2.6Ghz) that plays back HD without XvMC (it is  hyperthreading).  As buggy as XvMC can be, I think you might have a shot playing back HDTV on that Celeron. I know others have done it with Athlon XPs around 2.0Ghz. You might be pushing it though...

As far as it being able to handle playback or live playback - well, it if does one it will probably do both. Capturing HDTV streams isn't very processor intensive, so it won't have much of an effect on playback. So your machine could handle two digital tuners easily. P4 2.6ghz has 3 digital tuners in it.

No your system is plenty strong enough to do software encoding of the analog signal. A PIII 700Mhz could. But the quality is usually worse than a hardware encoder, and many people have had trouble getting the analog side of the pchdtv 5500 to work properly in myth (especially with the audio). I used to have one of those cards, and the audio only worked sometimes - I never spent the time to figure it out, as I sold the card and bought two less expensive cards (Kworld ATSC 110s) that could do the same thing, but I no longer use them for analog at all. I just use a PVR-150. Easy setup, good quality, and allows me to capture from other sources via S-video in.

To test, you could just install linux, setup XvMC, find an HDTV mpeg2 file to test and try playing it.

Also, transcoding HD to a space saving format with your processor will take hours for one show.

---

### Post by Angel700 on 2007-11-05
> **newlinux said:**
> I can't speak directly to the celeron, but like meph1st0 I have a P4 (2.6Ghz) that plays back HD without XvMC (it is  hyperthreading).  As buggy as XvMC can be, I think you might have a shot playing back HDTV on that Celeron. I know others have done it with Athlon XPs around 2.0Ghz. You might be pushing it though...

As far as it being able to handle playback or live playback - well, it if does one it will probably do both. Capturing HDTV streams isn't very processor intensive, so it won't have much of an effect on playback. So your machine could handle two digital tuners easily. P4 2.6ghz has 3 digital tuners in it.

No your system is plenty strong enough to do software encoding of the analog signal. A PIII 700Mhz could. But the quality is usually worse than a hardware encoder, and many people have had trouble getting the analog side of the pchdtv 5500 to work properly in myth (especially with the audio). I used to have one of those cards, and the audio only worked sometimes - I never spent the time to figure it out, as I sold the card and bought two less expensive cards (Kworld ATSC 110s) that could do the same thing, but I no longer use them for analog at all. I just use a PVR-150. Easy setup, good quality, and allows me to capture from other sources via S-video in.

To test, you could just install linux, setup XvMC, find an HDTV mpeg2 file to test and try playing it.

Also, transcoding HD to a space saving format with your processor will take hours for one show.

Thanks a lot, thats a big help.  I will probably just delete the video or  save it to another hard drive once i watch it so its no biggie about the transcoding.  I'll test out the HD like you said and post my results so others can see.

---

