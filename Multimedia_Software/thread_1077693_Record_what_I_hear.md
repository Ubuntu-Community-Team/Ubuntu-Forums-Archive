---
title: "Record what I hear"
date: 2009-02-22
forum: Multimedia Software
---

### Post by Franic on 2009-02-22
Hi all, 

What I'd like to do is recording what I'm hearing: for example some music is playing on my computer and at the same time it is recording to a WAV file.

It's NOT an hardware limitation because I can do it on Windows XP with Audacity... unfortunately I can't do it on Kubuntu (I can only record from my microphone).

My laptop is an Asus Z92J and my audio chipset is HDA Intel (weird but I use Realtek drivers on Windows). My OS is a Kubuntu 8.10 with KDE 4.2

Here is what I have:
```
franic@franic-laptop:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC880 Analog [ALC880 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC880 Digital [ALC880 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 6 : Si3054 Modem [Si3054 Modem]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```

```
franic@franic-laptop:~$ cat /proc/asound/devices     
  2:        : timer                                  
  3:        : sequencer                              
  4: [ 0- 6]: digital audio playback                 
  5: [ 0- 6]: digital audio capture                  
  6: [ 0- 2]: digital audio capture                  
  7: [ 0- 1]: digital audio playback                 
  8: [ 0- 0]: digital audio playback                 
  9: [ 0- 0]: digital audio capture                  
 10: [ 0]   : control
```

And a KMix screenshot, all the channels are shown:
[IMG]http://wisdomfranic.free.fr/data/unix/hda_intel.jpeg[/IMG]
According to KMix I'm using ALSA.

I've tried with no luck:
```
arecord -f cd -t wav -d 20 -D hw:0,0 machin.wav
arecord -f cd -t wav -d 20 -D hw:0,2 machin.wav
arecord -f cd -t wav -d 20 -D hw:0,6 machin.wav

```
Of course it doesn't work with Audacity with any recording device ><

If I can record the sound with Audacity it would be awesome, but I was just wondering: is there any way to redirect ALSA output to a WAV file? I don't care if I'm not hearing what I'm recording.

Help would be appreciated :)

---

### Post by Franic on 2009-02-23
Nobody to help me? Here's what I've tried:
Jackd -> I can't redirect what I want
Pulseaudio -> Doesn't work (founds no sound device and my multimedia keys don't work anymore)
.asoundrc -> Works with some apps, but not the ones I want (especially Firefox, and yes even with aoss)

Maybe I can do it with Phonon or Dmix, but I don't have a clue...

Please help me, that's really frustrating :/

---

### Post by mocha on 2009-02-23
Did you look at my guide for doing this and the link within my guide which goes to a great post on setting up PulseAudio and Jack?

[http://ubuntuforums.org/showthread.php?t=986966]("http://ubuntuforums.org/showthread.php?t=986966")

If you already followed the guide on setting up PulseAudio correctly AND assuming Alsa is working properly AND your hardware is working properly, then it should be very easy.

BTW, look in my guide for the PulseAudio guide link and check out what it says about Audacity.  You'll have to set it up to use Jack.  I prefer arecord for recording and Audacity for editing only.

---

### Post by Franic on 2009-02-23
I didn't know this HOWTO thanks a lot :) I've followed the HOWTO to setup Pulseaudio from the official French Ubuntu website and it didn't work.

If I need Pulseaudio then my multimedia keys won't work anymore but that's worth a try.

---

### Post by Franic on 2009-02-23
Okay so the multimedia keys issue is gone (it's because it could'nt connect to Pulseaudio nor ALSA... so it switched to OSS which doesn't support the PCM mixer for me).

I've combined your HOWTOs with the French one and now even Firefox is using Pulseaudio... great. I'll try Jackd now :)

Thanks for your help, hopefully it will work ^^

---

### Post by Franic on 2009-02-23
Sorry for the triple post but now it's solved :)

Unfortunately it didn't work with Jackd (no sound at all). But I've followed a tutorial only available in Google cache, so I'll explain it here.

First the music you want to record has to be seen in Pulseaudio Applet->Volume Meter (for Firefox for example I have ALSA plug-in [firefox]: ALSA Playback).

Then you have to know the name of the output device, so you type:
```
pactl list | grep Name: | grep monitor | sed "s/Name: //"
```
And you have the name. For me it is alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor

Now make an executable script which has:
```
#!/bin/bash
parec -d alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor > test.raw
``` 

Run the script on the terminal, play the music, then type CTRL+C on the terminal to stop the script.

Then to convert the RAW sound to WAV, type:
```
sox -w -s -L -r 44100  -c 2 test.raw test.wav
```

That's it, you can edit it with Audacity and do whatever you want. By the way the quality is quite good (like the "original" stream) I'm impressed ;)

---

