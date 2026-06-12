---
title: "Turtle Beach Audio Advantage SRM issues"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by comradburk on 2007-11-02
I just installed Ubuntu and have been trying to get my sound to work.  I have a USB Turtle Beach Audio Advantage SRM for sound output on my laptop.  I have USB selected in the System>Preferences>Sound menu and also changed my default audio device to "Audio" (the name of the USB device) in asoundconf but am still getting no audio in xmms/amarok etc.  In xmms though, when I changed the output plugin to ALSA and the default device to the USB sound card, I then received a message telling me it "Couldn't open audio.  Please check if your soundcard is configured properly/correct output plugin/no other program blocking the soundcard."  The only thing that seems to work is the test tone played in System>Preferences>Sound...any advice or things I might've missed?  I'm fresh out of ideas...thanks :)

---

### Post by comradburk on 2007-11-02
Nevermind...it works like a charm!  :)  I'm not sure what I did, but I just turned on my computer this morning after messing around with it last night and it's working now :)

---

### Post by Ansible on 2008-01-31
Looks like a nifty device.  I'm thinking of purchasing one of these for a low power NAS/audio server, which I want to leave connected to my home theater preamp all the time.  Under ubuntu, do you get surround sound from it through the s-pdif connection?

---

### Post by sacredpotato on 2008-03-28
I have the Ear Force AK-R8 model that also uses the ARM for a sound card and I have a few questions... for starters I haven't used linux since at least 2001 probably longer :-( and I never was very good at it



I have audio in DVDs (2 channel stereo) but the device is supposed to be a 7.1 surround device
I have MP3s and all that good stuff

all I have is the default usb audio drivers is there a driver I can get to get more functionality from ym card? 


also I have no audio in flash videos in firefox (i.e. youtube)

also I tried a quicktime movie in firefox and it played ok but about half way through the audio desynced  ... not really worried about that though... but not having youtube is killing me ;-)


any help would be appreciated... I know 8.04 comes out soon and maybe that will fix my problem but I've been googleing and reading these forums and others for 3 days and have done so many things I don't even know what I've done at this point



I'm desperate and totally lost please help


thank you so very much in advance

---

### Post by sudocat on 2008-07-15
comradburk, any chance you could describe what you did to get the Turtle Beach audio working w/Ubuntu? Or should I just mess around with a bunch of audio files, go to bed, and wake up hoping it works?

A list of the files you edited might be enough for me to get going.

---

### Post by comradburk on 2008-07-23
It's been awhile, lemme look on google for a bit and post back...I ended up not using it though because I didn't get the results I wanted.  I wasn't able to get surround output through the spdif for movies and stuff like that, so I just gave up and ended up just using my speakers (logitech z-5500's) to upmix the standard stereo out on my laptop.  I did get analog 5.1 audio to work correctly though...I'll post back in a minute after looking around and finding the sound settings I changed...

EDIT:
Alright, this thread is useful: [http://ubuntuforums.org/showthread.php?t=379429](http://ubuntuforums.org/showthread.php?t=379429) because it relates to USB audio

You need to make sure asoundconf has the USB sound card set up as the default.

```
asoundconf list

asoundconf set-default-card <Audio Device>
```

I remember doing that...that'll show you your sound devices, then replace <Audio Device> with the correct USB related one.  I also think I set all all the sound playback selections and stuff in System -> Preferences -> Sound   USB Audio or something like that. That was a long time ago when I got this working, so I dunno what else I did really...google was the biggest help.  The going to sleep and waking up later and hoping it works option is nice too :p that's what I did :)

---

