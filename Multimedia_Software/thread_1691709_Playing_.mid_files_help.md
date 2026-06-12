---
title: "Playing .mid files help"
date: 2011-02-20
forum: Multimedia Software
---

### Post by HappyLinux on 2011-02-20
Hello folks, I've got a problem that took me by surprise.

I've got hundreds of audio files in .mid file formats. I can get them to play fine under Windows using Windows Media Player and VLC, however, I cannot get them to play in Ubuntu 10.10.

This is strange really because VLC won't play them under Ubuntu. RythmBox and Music Player which came with Ubuntu seem to play the files, but without any sound.

Doing a quick Google on the matter, I find results which are confusing. Some say to use certain programs, some say to build a codec.

I need an answer that's straight forward. I still haven't got round to learning Terminal Command Line language yet.

What program is there that I can simply install and can play the files straight up? Or is there a codec for VLC which I need to install? And how do I do so? Or is it just not possible to play them under Linux?

---

### Post by andrew.46 on 2011-02-21
vlc will play midi files but it needs to be compiled against libfluidsynth and there must be suitable sound fonts installed on the system. Some info here:

MIDI with VLC media player
[http://www.remlab.net/op/vlc-midi.shtml](http://www.remlab.net/op/vlc-midi.shtml)

I attach a screenshot showing my own copy of vlc playing [this midi file]("http://samples.mplayerhq.hu/A-codecs/suite/MIDI/canyon.mid"), the audio visualisation is goom :).

Andrew

---

### Post by HappyLinux on 2011-02-21
Sorry, I haven't the foggy idea what you mean. There's all these files that are required and then I've got to compile at least 2 things alongside each other. It makes no sense to me in more ways than one.

---

### Post by andrew.46 on 2011-02-21
My apologies for increasing the confusion. What I was trying to say is that vlc is more than capable of playing back midi files but the packages available to Ubuntu users either from the Ubuntu Repositories or from most PPA's have not been set up to allow midi playback.

Options for you are either to hassle the Ubuntu packagers to package vlc with this capability, find a PPA with vlc setup in this way or embark on a very steep learning curve and learn to compile your own copy of vlc from its source.

Perhaps others reading this thread may know of a PPA that has vlc packaged in this manner? I am afraid that my own copy is compiled from source and I am not aware of such a PPA :(. Once you have a copy of vlc compiled in this manner (against libfluidsynth) it is a simple matter to get the midi files playing...

Andrew

---

### Post by HappyLinux on 2011-02-22
> **andrew.46 said:**
> My apologies for increasing the confusion. What I was trying to say is that vlc is more than capable of playing back midi files but the packages available to Ubuntu users either from the Ubuntu Repositories or from most PPA's have not been set up to allow midi playback.

Options for you are either to hassle the Ubuntu packagers to package vlc with this capability, find a PPA with vlc setup in this way or embark on a very steep learning curve and learn to compile your own copy of vlc from its source.

Perhaps others reading this thread may know of a PPA that has vlc packaged in this manner? I am afraid that my own copy is compiled from source and I am not aware of such a PPA :(. Once you have a copy of vlc compiled in this manner (against libfluidsynth) it is a simple matter to get the midi files playing...

Andrew

A single person hassling the Ubuntu packagers to do such a thing is like trying to knock down a reinforced wall with nothing but a feather duster. If someone knew a PPA that would help, then they would have mentioned it by now.

Therefore, I'm basically out of luck.

---

