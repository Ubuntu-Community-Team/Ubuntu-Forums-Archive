---
title: "Please, please, please help with microphone"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by ashinshanghai on 2007-10-24
Is there no one out there who can help fix a microphone problem??? I'm quite desperate as I am living overseas and cannot talk to my wife and colleagues back in the US. Also, I'm noticing many, many, many posts of similar problems in this forum that are going unresolved.

My problem is that neither the microphone in the built-in webcam nor the microphone in line input are working. I can't use skype, and I can't record anything using Sound Recorder.

In my volume control, everything is enabled; everything is unmuted and the volumes are up.

I recompiled alsa on advice of some other posts. No change.

I am running Gutsy now, and this problem carries over from Feisty. No change after upgrade.

I have an HP dv1000t laptop with HDA intel card. 

Pretty please developers who may have worked on this, a lot of people here need your help!

---

### Post by SIGINT23 on 2007-10-24
Are you in theater? If yes, ask one of your signal folks to fix your issue. If you are overseas in any other business, try installing gnome-alsamixer.
Besides, you can searched your webcam model with the word ubuntu under google and see what comes up.

---

### Post by NilsE on 2007-10-24
I am sure you have tried this but just incase.

In a terminal run: asoundconf list

This should return a list of cards.

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then **again with sudo**: sudo asoundconf set-default-card xxxxx
 
This will set the defaults for the card and create a config file. 

Replace   xxxxx  with the name you found in list.

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can that show up on all of the tabs. Make sure none are muted.

---

### Post by ashinshanghai on 2007-10-24
> **NilsE said:**
> I am sure you have tried this but just incase.

In a terminal run: asoundconf list

This should return a list of cards.

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then **again with sudo**: sudo asoundconf set-default-card xxxxx
 
This will set the defaults for the card and create a config file. 

Replace   xxxxx  with the name you found in list.

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can that show up on all of the tabs. Make sure none are muted.

Yep, tried these. Then in Preferences>>Sound I tried to test sound capture and I get the error:

```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

Unfortunately I am not in theater and have no sound people to consult. The webcam camera is working (it's a Ricoh with restricted driver).

Thanks for these suggestions, tho.

---

### Post by h2z on 2007-10-24
Having the same problem with the mic - I have the boost on and the mic's volume is at 100% but when I try recording my voice I get nothing (sound output is working fine, I also have multiple sounds from different programs), I've tried all the options under the "sound capture" drop down box but I keep getting these errors: (Default mixer tracks set to ALSA and so it everything for sound output/playback)

This is with the options set to "ALSA - Advance Linux Sound Architecture" and "ALI M5455"
```

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

```

Option set to: "ALI M5455 - MIC ADC" and "OSS - Open Sound System"
```

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

```

I'm using an on board Realtek ALC850 Audio AC'97 Codec (Mobo is using ULi M1689 chipset) which is detected by the system:

```

stefan@stefan-linux:~$ asoundconf list
Names of available sound cards:
M5455

stefan@stefan-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by NilsE on 2007-10-24
I have to ask:

1) When you did the asoundconf set-default-card did you do it without the sudo and then again with the sudo?

2) Did you select all of the IEC switches on the Switches tab?

3) The right source for the mic on the options tab?

4) Do you see more than one sound card in the list?

---

### Post by h2z on 2007-10-24
Well I have changed anything from the ubuntu installetion but I have been able to choose the ALSA driver for all of the outpud and input drop down boxes :S I've tried all available options for the mic input and there is only sound card listed...

---

### Post by ashinshanghai on 2007-10-24
> **NilsE said:**
> 
1) When you did the asoundconf set-default-card did you do it without the sudo and then again with the sudo?

Yes

> **NilsE said:**
> 2) Did you select all of the IEC switches on the Switches tab?

Yes

> **NilsE said:**
> 3) The right source for the mic on the options tab?

I don't have an "options tab" per se. In the volume control, I have a "playback," "recording," and "switches" tabs. On Playback there are controls for: Headphone, PCM, PCM-2, Mic Gain, and Speaker. On Recording there are: Mic Bypass, Capture, and Digital. On Switches: a checkbox for IEC958. 

Under Volume Control>>Edit>>Preferences I have everything enabled. Under File>>Change Device I have HDA Intel selected. There is also an option here for Conexant CX20551 (Waikiki) (OSS Mixer). 

Those are the only options I have there.

Under System>>Preferences>>Sound>>Devices Tab>>Audio Conferencing>>Sound Capture I have ALSA selected.
> **NilsE said:**
> 4) Do you see more than one sound card in the list?

No

---

### Post by tiki999 on 2007-11-10
> **NilsE said:**
> I am sure you have tried this but just incase.

In a terminal run: asoundconf list

This should return a list of cards.

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then **again with sudo**: sudo asoundconf set-default-card xxxxx
 
This will set the defaults for the card and create a config file. 

Replace   xxxxx  with the name you found in list.

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can that show up on all of the tabs. Make sure none are muted.

Thank you, it solved my problem :)

---

### Post by wilerk on 2007-11-16
HI all,

This fix seems to work although the sound for my mic is still very soft even if I adjust the scrollers. 

Forgive me if this sounds stupid but this procedure tells me I have an intel sound card, so why do I install realtek drivers when I'm using XP?

Thanks,

Xander

---

### Post by RTrev on 2007-11-16
> **wilerk said:**
> HI all,

This fix seems to work although the sound for my mic is still very soft even if I adjust the scrollers. 


This is my problem also.

My sound is very strange.  I can turn up the volume with the mike connected and get feedback,  and can loudly hear the sound through the speakers when I tap on the mike.  Yet when I use Sound Recorder, the volume of the recording is so low that even turned up to full volume I can just barely hear it.  So the signals are getting through, I've done all suggested above, but cannot get any volume on the recording of the microphone.

Ideas??

Thanks,
Bob

---

