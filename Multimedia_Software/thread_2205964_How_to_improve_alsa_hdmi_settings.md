---
title: "How to improve alsa hdmi settings?"
date: 2014-02-16
forum: Multimedia Software
---

### Post by PeterTaps on 2014-02-16
Folks,

Environment: Ubuntu 13.04 bare bones + OpenBox + vlc. Pure alsa. No pulse audio installed.

I have an nVidia HDMI card in my box. The card is connected to my 5.1 receiver. 

When I run "speaker-test -c6 -Dsurround51 -twav," it doesn't work.

After searching through various forums, I defined the following settings in .asoundrc.

pcm.!hdmi {
     type             route
     slave.pcm
 "cards.HDA-Intel.pcm.hdmi.0:CARD=NVidia,AES0=0x4,AES1=0x82,AES2=0x0,AES3=0x2"
     ttable.0.0 1
     ttable.1.1 1
     ttable.2.4 1
     ttable.3.5 1
     ttable.4.2 1
     ttable.5.3 1
     ttable.6.6 1
     ttable.7.7 1
 }

Using speaker-test, I can test each individual speaker in my 5.1 setup and everything seems to work.

However, I am wondering if I lose any quality by using "route." The reason I am saying this is because by box is a dual-boot system and the same .mp4 file when played through vlc in Windows seem to sound better.

Can there be a better alsa setup?

Thank you in advance for your help.

Regards,
Peter

---

### Post by TheFu on 2014-02-17
* 10.04 desktop support ended about 2 yrs ago.
* **aplay -l** please.
* Which driver is used for the audio?  F/LOSS or proprietary? Is it the most current?
* What audio encoding does that 1 test file have?  That can matter if the Linux driver doesn't support some of the higher end encodings like TrueHD.


Also, [this guy says to purge pulse-audio]("http://www.audiomisc.co.uk/Linux/ALSA/NoMoreSilence.html") from the system.

---

### Post by PeterTaps on 2014-02-17
It was meant to be 13.04, not 10.04. Sorry for the mistake. I have corrected my original post.

I have installed the latest nvidia driver "apt-get install nvidia-current."

My .asoundrc setting works. I am just wondering if "route" deteriorates the performance and if I should really be using some other settings.

Regards,
Peter

---

### Post by TheFu on 2014-02-17
13.04 support ended last month.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Non-LTS releases have fairly short support periods.  Best to install and stay with only LTS, IMHO - unless you are a developer then I'd even MORE strongly try to get you to only use LTS!  

Just because we think we're using alsa, that doesn't mean that pulse isn't getting in the middle and screwing with the quality. Just sayin'.

Can't speak about route ... but if we consider what that is normally used to accomplish, I could see where merging outputs could reduce quality. Still I don't know anything for certain.  More processing usually means more complexity and that means more chances for mistakes.  Backup the .file and try it without the route - how does it sound?

---

