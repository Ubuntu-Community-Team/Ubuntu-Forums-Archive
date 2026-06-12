---
title: "enable-remixing = no (turning off remixing seems to kill true 5.1 audio?)"
date: 2018-02-07
forum: Multimedia Software
---

### Post by krummie on 2018-02-07
Hi Guys,

Running Ubuntu 16.04 on a Intel NUC as a HTPC, connected to my receiver through HDMI.

When playing videos where the audio is stereo, I'm getting sound in all my speakers, which I don't want.  Doing some research I found a thread here that appeared to fix my issue:
[https://ubuntuforums.org/showthread.php?t=1561695](https://ubuntuforums.org/showthread.php?t=1561695)

I set enable-remixing = no and rebooted.  Played the video, and perfect!  I'm only getting audio from the front now from my videos with stereo audio.

Now here comes the issue... that setting appears to have turned off the surround sound in general.  I tried playing some videos that have 6 channels (5.1), and I'm getting zero sound from my rear speakers.  The media player (Plex) is telling me it's outputting 5.1, and I know its 5.1 because I can look at it's properties, plus I've seen the videos before using other hardware like my bluray player with usb input.  I double checked the system output setting, and its still listed at 5.1 hdmi.  My receiver is telling me it's picking up the 6 channels from the output (and it says that even when the audio is stereo - I'm assuming because the system output is set to 5.1, no matter what is sent, it sends all the channels even if not used).

I thought maybe all along all my devices were upmixing, but I can't believe videos labeled at 5.1 (and physically show 6 channels in the properties) have zero back sounds.  Especially on a war movie where you should hear bullets and mortars go from the front speakers to the back as they fly by.

I feel like every time I "fix" one problem, I just break something else.  Of course if I turn remixing back on, my 5.1 videos work again, but then I'm stuck with my 2.0 audio videos outputting sound in all my speakers.

This one is confusing me as I don't see why a remixing setting would make what should be natural 5.1 source (which shouldn't need remixing...) stop working.

Any ideas?

Thanks!

---

### Post by #&amp;thj^% on 2018-02-07
As your already aware, With that setting only native 5.1 apps produce surround sound.
have you played with Kodi yet?

---

### Post by krummie on 2018-02-07
Yep.  That's the confusing part, as Plex (it supports almost all codecs) does play 5.1 audio, and is telling me it is when I look at the details when it's playing.

Maybe I will try Kodi, but my guess is it would be the same result.

---

### Post by #&amp;thj^% on 2018-02-07
> **krummie said:**
> Yep.  That's the confusing part, as Plex (it supports almost all codecs) does play 5.1 audio, and is telling me it is when I look at the details when it's playing.

Maybe I will try Kodi, but my guess is it would be the same result.
have a look here for setting up Kodi <Hint Passthrough>: [https://kodi.wiki/view/PulseAudio#Passthrough_Mode](https://kodi.wiki/view/PulseAudio#Passthrough_Mode)
Sound on Linux is perplexing and fun, once you get your head wrapped around it. :D
Good Luck and welcome to the forums.;)

---

