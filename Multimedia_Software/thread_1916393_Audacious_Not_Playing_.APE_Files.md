---
title: "Audacious Not Playing .APE Files"
date: 2012-01-27
forum: Multimedia Software
---

### Post by juantendo8 on 2012-01-27
Hello, I have been using audacious as my main music player and only now just realized that it is not reading my .ape files. I was under the impression that audacious natively supported this format. I don't remember this being a problem in the last Ubuntu version. What am I missing?

---

### Post by Rodney9 on 2012-01-28
For codecs extra I always go to  -  

[http://ubuntuforums.org/showthread.php?t=1884105&highlight=lmms](http://ubuntuforums.org/showthread.php?t=1884105&highlight=lmms)

Rodney

---

### Post by mc4man on 2012-01-28
You haven't mentioned what release of ubuntu you're using. If on 11.10 (Onieric) then audacious was not done too well.

In that case you might want to consider this ppa which will give you the latest 3.2.1 audacious. 

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

Before doing so maybe download & test with the .ape  from here which plays in aud just fine on my current aud

[http://samples.mplayerhq.hu/A-codecs/lossless/](http://samples.mplayerhq.hu/A-codecs/lossless/)

---

### Post by juantendo8 on 2012-01-28
Thank you very much for pointing out this problem in 11.10. Indeed, I updated to the latest audacious, and I have fully functional use again. Thanks once again.

---

### Post by mc4man on 2012-01-28
The ppa should take care of having complete audio decoding support in aud, there isn't any movement towards fixing this, why?, no clue

In 12.04, which just got the 3.2.1 aud the same deal, no ffaudio support. Really no excuse.

For curious - 
bug in 11.10
[https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/880192](https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/880192)
bug refiles for 12.04 - 
[https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/922985](https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/922985)

Min. affected decoding support - .ape, .wma2, .wma3, .mpc, .tta

---

### Post by andrew.46 on 2012-01-29
@mc4man: I have learned to love audacious and I was pleasantly surprised to learn in another thread on these Forums that midi playback is possible by compiling against libfluidsynth and providing a soundfont. Great audio player :).

---

### Post by mc4man on 2012-01-29
> **andrew.46 said:**
>  I have learned to love audacious and I was pleasantly surprised to learn in another thread on these Forums that midi playback is possible by compiling against libfluidsynth and providing a soundfont. Great audio player :).

It is an excellent player, when I still had a desktop with 5.1 digital out sound the combo of aud & mplayer handled various audio files perfectly, stereo as stereo, surround as surround (vlc-1.2+ also was good there.

While no excuse whatsoever, (the fix takes all of a min to implement, if that), the recent & current lack of ffmpeg support in 11.10 & 12.04 can be traced to Debian/Ubuntu using Libav while the aud source is basing off of FFmpeg


Considering that the Debian 'ffmpeg' maintainer was in the orig. split/takeover group, I'd say Libav is here to stay

---

### Post by shantiq on 2012-01-29
> **mc4man said:**
> 

In that case you might want to consider this ppa which will give you the latest 3.2.1 audacious. 

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)




thnax for that was wondering   why Audacious had nothing left in it

this ppa brings back   crystalizer   which is such an amazing filter/effects plugin/enhancer  :KS    got to be heard 

[preferences/plugins/effect]

---

