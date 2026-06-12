---
title: "Jackd crashes on mp3 playback"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by pppZero on 2007-07-16
I just came from Gentoo, where I had the same setup running fine:

I followed [http://ubuntuforums.org/showthread.php?t=491984](http://ubuntuforums.org/showthread.php?t=491984) to get sound out of alsa apps into jack, which is also then routed into jack-rack with jack.plumbing

Sound follows this path on my system:
<Sound App>
  -> Alsa
  --> Jack
  ---> Jack-Rack running SC4 Compressor + volume
  ----> Soundcard

But now I have problems with some apps...

 o Totem works fine, music and video, but has native jack support.
 o Amarok (via the xine engine, which uses alsa) works perfectly. plays music all day and all night.
 o Xine plays movies perfectly (with sound), but will Barf on straight audio files.
 o Mplayer will Barf, with movies or just audio.
 o Firefox (youtube, et al) will Barf, then crash(!).

Definition of "Barf":
Same symptom everywhere here. Sound works fine for about 5 seconds, Sound output stops, jackd complains about an XRUN, jackd segfaults, audio app will continue trying to output sound, but not get anywhere.

I have tried rebuilding libsound via the above link. I've tried a minimalist .asoundrc. I've tried different sample rates in jackd. I even threatened to take the coffee away from it, but ultimately, I got nowhere. 

I'm fairly certain libasound is where things are going wrong, but how I'm just not sure. :(

My Soundcard is a Live 5.1, on Feisty, updated this morning.

If anyone has any thoughts on whats going on here, please throw your $0.02 into the ring, I'll take anything upto, and including "train a monkey to play guitar and take up busking" - Its driving me insane :(

---

### Post by fredj on 2007-07-16
Well you don't give us much information to go  on. If you want jack to work really well then you have to
install the real time kernel and tweak your system to give jack a high priority.

---

