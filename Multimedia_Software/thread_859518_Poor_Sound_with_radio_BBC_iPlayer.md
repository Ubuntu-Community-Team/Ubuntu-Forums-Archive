---
title: "Poor Sound with radio BBC iPlayer"
date: 2008-07-14
forum: Multimedia Software
---

### Post by Philip Farrugia on 2008-07-14
Since BBC has moved radio to the iPLayer I get a strange echo-ing on the live broadcasts.  Before I cured this by using RealPlayer but iplayer refuses to find RealPlayer and I can only get Totem plug in to work but with a strange sound effect.

I'm running Firefox3 and Hardy Heron. RealPlayer11.

Ideally I want to cure the following error message "Could not find an appropriate hxplay or realplay in the system path to use as an embedded player".

Alternatively get mplayer or totem to play the live stream correctly.

Any ideas anyone?

---

### Post by markbuntu on 2008-07-14
How about a link to the url so we can try it out?

---

### Post by quill3033 on 2008-07-15
It seems to be working fine for me in a pop up window since I installed (just now) Helix and the helix mozilla plugins - before that it kept asking me to download realplayer for linux. hope this helps. I find the sound is really good.

---

### Post by silkstone on 2008-07-15
Assuming you haven't already got all this...

sudo apt-get install alsa-oss gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll w32codecs

---

### Post by gandaran on 2008-07-15
> **Philip Farrugia said:**
> Since BBC has moved radio to the iPLayer I get a strange echo-ing on the live broadcasts.  Before I cured this by using RealPlayer but iplayer refuses to find RealPlayer and I can only get Totem plug in to work but with a strange sound effect.

I'm running Firefox3 and Hardy Heron. RealPlayer11.

Ideally I want to cure the following error message "Could not find an appropriate hxplay or realplay in the system path to use as an embedded player".

Alternatively get mplayer or totem to play the live stream correctly.

Any ideas anyone?

Philip Farrugia
bbc has live radio streams in real audio and wma.
real-player11 plays real audio and video, have you run the commands to get real-player embedded in firefox?
totem-gstreamer works with wma audio, only totem-xine will play both wma and real audio (which I think is the best solution), mplayer is not the best solution for the bbc site, some times it fails to connect to the stream.

---

### Post by ZootNerper on 2008-07-21
Hi,

I have a problem with whatever the default player/plugin is for the BBC iplayer, after a few minutes it starts to stutter and chunks of sound go missing.

If I look in the Firefox Preferences->Applications, I can't see any reference to RealPlayer file types (I believe they are *.rm). I maybe looking for the wrong type. I was looking to see if I could substitute Totem-xine for whatever runs the BBC iPlay (as suggested by gandaran above).

What do I need to change or do?

I run Hardy Heron with all updates, I don't have RealPlayer installed.

-- Zoot

---

