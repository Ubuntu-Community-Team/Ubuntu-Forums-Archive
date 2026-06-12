---
title: "M-Audio Revolution 5.1 problems"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by krusk on 2006-03-09
Hey

I am having problems with getting the card ro work properly in breezy. It seems like all the drivers and modules load correctly. I get sound in all programs and players, but the sound is really bad; it is twisted and distorted.

alsamixer is also weird, it has very few options and it seems like irrelevant for my problem. this problem is also described here:
[http://www.ubuntuforums.org/showthread.php?t=108253&highlight=m-audio]("http://www.ubuntuforums.org/showthread.php?t=108253&highlight=m-audio")

my sound problem seems to be described here, disappointingly with no replies:
[http://www.ubuntuforums.org/showthread.php?t=118399&highlight=m-audio]("http://www.ubuntuforums.org/showthread.php?t=118399&highlight=m-audio")
This is another soundcard, but the sam chip, ICE1724.

After reading some posts about the envy24control program, I figured it might helpme. But it refuses to start, saying i don't have a ICE1712 chip. Is it impossible to get this program to work with ICE1724? (I had to install dapper drake and install alsa-tools via apt-get to get this program)

I have tried to boot the cards in other distroes (mepis, dapper) and the problem remains the same. I get sound, but a non-listening one.

I found out by coincidence that the startup sound in the game bugsquish gives almost no distortion, the sound is almost normal. This program uses 22050 Hz 16-bit stereo. I think this may be important, cause all my mp3 and wav is 44 kHz (unsure of the bitrate). Maybe the card isn't correctly set up for 44 kHz playback, or something? Any way to adjust this? 

Any ideas, to either one of these concerns, are highly appreciated! have been stuck working with this problem for a while... Thanks!

---

### Post by rimsy on 2006-04-22
Hi, I have exactly the same problem. I've tried envy24control with the same results and I also suspect that some 22-odd kHz sampling rate is locked in the card's control registers :D. Did you come up with something? I've been stuck with this since I first tried breezy... Thanks.

Cheers
Pete

---

### Post by hotani on 2006-04-23
Just chiming in with the exact same problem here. Can't seem to get anything but garbage out of my M-audio Revolution 5.1 soundcard.

(ubuntu 6.06 beta, PPC)

---

### Post by hotani on 2006-04-30
This seems to be fixed with the latest Live CD 6.06 Beta 2 - woohoo! :)

---

