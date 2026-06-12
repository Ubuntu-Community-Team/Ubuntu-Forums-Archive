---
title: "Cant Play Any Media Files."
date: 2009-02-21
forum: Multimedia Software
---

### Post by ku5165 on 2009-02-21
A new problem occurred today :(
I guess I should stop tinkering so much with Ubuntu, but I learn by tinkering.

Oh well, now onto the problem, I can't play any media files (.avi, .mp3) the player (totem & rhythmbox) freeze right when I click play. The rest of the computer seemingly works fine.

So I checked codecs, and tried different programs yet nothing works.
The only changes I had made to the system (which is what I believe had contributed to this problem) are installing EasyTag, and Picard (mp3 tagging tools), however, I did not like easytag, so I preceded to remove it and also did autoremove to remove any dependencies I had installed with it. 

And after this nothing would play, so I am guessing it is some incompatibilities, (I had edited a few tags, but none of my songs play). I have uninstalled Picard also hoping it would recover my problem, yet that did not work.

I am guessing something somewhere got removed that shouldnt have been.

Oh I had also added some sources (to install both the programs, and I had also removed these sources afterwards). One of the sources I had added was Debian 5.0 "Lenny" which ended up giving me some 400+ updates, therefore I removed it being scared by all the items that had shown up (are those updates better than the ones in Ubuntu Updates???).

Please help me restore my music.

Thanks in advance
Ku

P.S. 
I am running Ubuntu Intrepid Ibex 8.10 with all latest updates (except for those suggested by one of the sources)

Let me know if you need any other information.
Ku

---

### Post by ku5165 on 2009-02-22
Please someone help me :( its not fun being able to not use ubuntu to watch movies and listen to music.
Thanks in advance

---

### Post by xc3RnbFO8P on 2009-02-22
Try in Terminal:
> totem
and play something.
Show the output if get some errors messages.

---

### Post by ku5165 on 2009-02-22
> **Ringi said:**
> Try in Terminal:

and play something.
Show the output if get some errors messages.

I get this, does that mean im missing pulseaudio? If so how to reinstall it?
Thanks for your help
Ku

```

** (totem:21093): DEBUG: Init of Python module
** (totem:21093): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:21093): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:21093): DEBUG: Creating Python plugin instance
** (totem:21093): DEBUG: Init of Python module
** (totem:21093): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:21093): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:21093): DEBUG: Creating Python plugin instance
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(634): gst_pulsesink_prepare (): /GstPlayBin:play/GstBin:visbin/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin6/GstAutoAudioSink:autoaudiosink1/GstPulseSink:autoaudiosink1-actual-sink-pulse 
```

---

### Post by ku5165 on 2009-02-23
please someone help me?

---

### Post by xc3RnbFO8P on 2009-02-23
Try, System >Preferences >Sound and changed the "Music and Movies" setting from "Autodetect" to "ALSA"

---

### Post by ku5165 on 2009-02-24
hey, thank you very much
that worked for me, not the alsa setting but tinkering with the sound preferenced helped alot...
Thanks once again.
ku

---

