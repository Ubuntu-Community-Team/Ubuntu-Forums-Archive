---
title: "Audio quality bad in jaunty but good in hardy"
date: 2009-08-06
forum: Multimedia Software
---

### Post by bricedebrignaisplage on 2009-08-06
I have both Hardy and Jaunty installed on my computer (mostly because I not totally satisfied with KDE4). One runs KDE3.5 and the other KDE4.x

Some of my mp3 don't play well under Jaunty: although they are encoded in good quality, the sound is really poor quality. Meaning that I am hearing lots of saturation (not sure whether it's the exact tech term to describe what I am hearing though). Across all players (tried mplayer, vlc, amarok, exaile).

The strange thing is that the same file, on the same hardware, plays really nicely in Hardy... And it's only some files, but I could not figure out the common factor.

Could it be hardware driver issues or a bug in mp3 decoder under Jaunty?

Sound card:
VT8233/A/8235/8237 AC97 Audio Controller
VIA Technologies, Inc.
driver=VIA 82xx Audio latency=0 module=snd_via82xx

---

### Post by martinbaselier on 2009-08-06
If it are only certain files, you can check the codec information in vlc to see the difference between them and the other files.

---

### Post by bricedebrignaisplage on 2010-01-04
I recently removed Jaunty and installed Karmic. I kept Hardy. There is the same issue under Karmic. Some audio files render poorly. I tried to check codec information, but could not find anything. All are mpga (MP3). sampling frequency and bitrate do not seem to have an effect on the result. Here is a link to one MP3 that does not play well on my Karmic installation, but plays nicely under Hardy. Hope somebody will be able to find the problem...
[http://www.bricerebsamen.com/rep/test.mp3](http://www.bricerebsamen.com/rep/test.mp3)

---

### Post by Marrkk on 2010-01-04
probably the fault of pulseaudio..
i rant about in my blog. :(



Mark


[http://marrcuk.blogspot.com/]("http://marrcuk.blogspot.com/")

---

### Post by bricedebrignaisplage on 2010-01-13
Some more info. I tested on my laptop (other hardware) under Sid (Debian) and with the Karmic Kubuntu live CD. Those MP3 files that play badly on my Karmic installation (desktop) play really well on my laptop under Sid and Karmic.

On my desktop, I tried with the live cd as well, to make sure that it was not an installation issue, and the audio quality is bad.

Following the links from previous poster, I found a guide to get rid of pulseaudio. I haven't tried it yet, but I doubt this is the issue. In the first place, I am not sure my audio system uses pulseaudio. In system settings > multimedia > music, pulseaudio is the last option, the first one being ALSA (x-phonon).

How can I know for sure what tool stream my audio system is using?

On my laptop the audio hardware is: Intel Corporation 82801I (ICH9 Family).
On my desktop (the one with the problem): VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

So I'm thinking, could it be a problem with the VIA drivers (snd_via82xx and snd_ac97_codec (?)) in Ubuntu post Hardy?

---

### Post by bricedebrignaisplage on 2010-01-14
I made some more investigations and I may have found what causes the problem. Apparently those problematic MP3 were recorded / encoded with a too high audio level. As such when they are reproduced at a high volume (master and pcm controllers in the mixer) they saturate the sound card, producing that ugly sound.

On my laptop I didn't experience any problem probably because I am playing at a lower volume. I need to test with high volume. I don't know why there was no problem under hardy though, maybe the new mixer adds more gain...

To confirm this I need to check what's the encoded volume in my MP3 files. How can I do this? And understand more about volume encoding...

Then a possible solution is to make sure that all my MP3s are encoded with approximately the same volume. That may mean re-encoding some of them. How can I do that, possibly without losing quality?

Hope somebody is listening and that I am not talking to myself...

---

### Post by bricedebrignaisplage on 2010-01-16
Using mp3gain to normalize the whole collection solved the problem.

---

