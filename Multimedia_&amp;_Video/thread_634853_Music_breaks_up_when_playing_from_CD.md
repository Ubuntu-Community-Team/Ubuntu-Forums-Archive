---
title: "Music breaks up when playing from CD"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by ron999 on 2007-12-08
Hi
When I play music CDs the sound crackles and breaks up.
Also when I rip tracks, they sound bad when I play them back.

I don't have any problems when viewing movie DVDs.
I don't have any problems when reading or writing data CDs and DVDs.

I've tried several media players (VLC, SoundJuicer, Rhythmbox etc) but they don't cure it.

Any ideas how to fix this?
:confused:
Edit. I can now get a CD to play using VLC > Open Disc > Audio CD
But I still can't rip tracks properly using SoundJuicer or K3b

---

### Post by logos34 on 2007-12-08
> **ron999 said:**
> Hi
When I play music CDs the sound crackles and breaks up.
Also when I rip tracks, they sound bad when I play them back.

I don't have any problems when viewing movie DVDs.
I don't have any problems when reading or writing data CDs and DVDs.

I've tried several media players (VLC, SoundJuicer, Rhythmbox etc) but they don't cure it.

Any ideas how to fix this?
:confused:
Edit. I can now get a CD to play using VLC > Open Disc > Audio CD
But I still can't rip tracks properly using SoundJuicer or K3b

playback distortion/crackling can be caused by the PCM volume being all the way up (i have to set mine for no more that ~87

$ alsamixer

Try the suggestions on [this page]("https://help.ubuntu.com/community/CDRipping#head-452073ae050f16886cc103fbbcc27963919f5724")?

K3b is a hard one to configure for ripping--I have yet to find a guide to the command line options for externel audio encoder (i.e. musepack)...can't always get it to rip lame/mp3 at specified settings

---

### Post by ron999 on 2007-12-08
Hi
Thanks for your reply.
I've checked the Alsa setting for PCM. It's OK.
When I play a CD in SoundJuicer or K3b I get the distortion and breakup. Installing the mp3 codecs won't help.
When I tried Amarok the CDs sounded OK but I couldn't figure out how to rip with it.
I'm fairly sure that I was able to play/rip with SoundJuicer and K3b in the past, but they're not behaving now.
I don't mind using VLC to listen to the discs, but I need something to extract WAV files from them.
:confused:

---

### Post by logos34 on 2007-12-08
> **ron999 said:**
> ... Installing the mp3 codecs won't help.
When I tried Amarok the CDs sounded OK but I couldn't figure out how to rip with it.

because it's not an mp3 issue

amarok doesn't rip or burn (although it has the latter menu option)--it connects to k3b which does.

> I don't mind using VLC to listen to the discs, but I need something to extract WAV files from them.

you might try grip...it can be hard to configure the encoder command line but if all you want to do is rip the .wavs then you should be able to do it right off the bat without any fuss.  

Or get abcde and do

abcde -a read

look in ~/abcde... folder

---

### Post by ron999 on 2007-12-08
I've had no luck with grip or abcde either.](*,)
Something's seriously the matter with my setup I think:confused:

I can rip cd tracks one at a time using vlc, but it's not very convenient.:???:
This method:-[http://flossmanuals.net/VLC/RipCD]("http://flossmanuals.net/VLC/RipCD")

---

### Post by logos34 on 2007-12-08
> **ron999 said:**
> I've had no luck with grip or abcde either.](*,)
Something's seriously the matter with my setup I think:confused:

I can rip cd tracks one at a time using vlc, but it's not very convenient.:???:
This method:-[http://flossmanuals.net/VLC/RipCD]("http://flossmanuals.net/VLC/RipCD")

yeah, maybe it's time to upgrade or better yet do a fresh install of 7.10 and hope that solves your problems

---

### Post by ron999 on 2007-12-13
Hi
I know that I'm about ready to upgrade to Gutsy, but in the meantime how can I diagnose this CD fault?
It's weird. Usually I can only get distorted sqeeks and distortion from Sound Juicer. But yesterday it was OK. I listened to some CDs and extracted them without trouble. But today it's bad again.
All the time, I can listen and rip CD tracks using VLC.
So what is it that's different with VLC compared to SoundJuicer, K3b, Grip etc?
:confused:

---

