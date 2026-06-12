---
title: "Cannot use anymore gnome sound recorder"
date: 2010-01-02
forum: Multimedia Software
---

### Post by premamotion on 2010-01-02
Hi everybody! Some time ago I had problems with PulseAudio so I removed it and now Alsa is managing greatly the sound. The problem is that when I removed PulseAudio, or when I have done something ( I don`t know what) I broke Gnome Sound Recorder, and now I`m unable to use it. It doesn`t matter which type of recording I choose (voice lossy, cd quality, voice lossless), the error is the same... Cannot record using the recording type that I choose, need to check the settings... Probably modules are missing... which modules do I need to make Gnome sound recorder work?

Thank you in advance, and best wishes!

---

### Post by Kimm on 2010-01-02
try installing Audacity for sound recording instead. I'm quite sure that Gnome Sound Recorder depends on Pulse or ESD.

You could try to install the "esound" package, though, thats deprecated software

---

### Post by premamotion on 2010-01-02
Thank you so much, Kimm! Tried with Audacity also, but for some reason I`m not able to record anything also with it... and I had installed esound package, and I saw no difference for my problem...

 Thanks again!!!

---

### Post by Kimm on 2010-01-02
You may have to play around with the audio settings in Audacity, under "Edit" you'll find "Preferences", there you can play around with the device settings for input and output.

The device you'll need to configure it for is most probably "hw:0,0" (or something similar, the name will probably not be this short) for both input and output.

The esound idea was a long shot :)

---

