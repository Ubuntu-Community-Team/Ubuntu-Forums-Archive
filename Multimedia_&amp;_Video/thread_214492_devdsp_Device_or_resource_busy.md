---
title: "/dev/dsp: Device or resource busy"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by derakhshani on 2006-07-12
I installed some sound applications after that audio editor applications which worked perectly some hours ago, report initialization error in startup. for example: 
> 
$rezound
using path '/usr/share/rezound' for share data directory
Error occurred while initializing audio output method 'oss' -- virtual void COSSSoundPlayer::initialize() -- error opening OSS device '/dev/dsp -- Device or resource busy
Error occurred while initializing audio output method 'jack' -- virtual void CJACKSoundPlayer::initialize() -- error connecting to jack server -- jackd not running?

rezound worked perfectly before, but now it is a garbage.](*,) 

the strange thing is that I can play music file via mplayer or rhythmbox without any problem.

I am realy confused.
any idea?

---

### Post by BitTorrentBuddha on 2006-07-12
It's because of how the sound card works, it can only play one source at a time. Ritzier cards mix all the programs' audio into one source on the card, older ones rely on software to mix it. ESD/Alsa will mix sound together and access the card. Rezound uses OSS instead, so you can use it if neither ESD nor Alsa are using the card (which is why it worked before.) The best bet would be to try and run it with alsa-oss (see below); if that doesn't work, and there's a good chance it won't, you can either buy a new sound card or make sure there's no other program using sound when you start it.
To use alsa-oss (*only run the first line the first time you want but always start rezound with aoss*):```
sudo apt-get install alsa-oss
aoss rezound
```

---

### Post by derakhshani on 2006-07-13
After rebooting before useing any audio apps sometimes rezound works sometimes does not. I installed alsa-oss.
after that:

```
$ rezound
using path '/usr/share/rezound' for share data directory
If rezound dies unexpectedly while seeking with the keyboard, auto-repeat may be disabled.. if this happens run 'rezound --fix-auto-repeat'

```

but:
```
$ aoss rezound
using path '/usr/share/rezound' for share data directory
Error occurred while initializing audio output method 'oss' -- virtual void COSSSoundPlayer::initialize() -- error setting the buffering parameters -- Invalid argument
Error occurred while initializing audio output method 'jack' -- virtual void CJACKSoundPlayer::initialize() -- error connecting to jack server -- jackd not running?
If rezound dies unexpectedly while seeking with the keyboard, auto-repeat may be disabled.. if this happens run 'rezound --fix-auto-repeat'
```

I think there are some more problems!
:-k ?

---

### Post by Ubuntnik on 2006-11-08
Rather than buy a new card, go into the Sound Preferences and disable software mixing - solved the problem for me where Totem would play files but Wavbreaker wouldn't (on Dapper).

---

