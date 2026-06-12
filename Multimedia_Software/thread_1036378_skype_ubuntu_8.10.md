---
title: "skype ubuntu 8.10"
date: 2009-01-10
forum: Multimedia Software
---

### Post by acmariner99 on 2009-01-10
How I can get no audio playback with skype, I tried uninstalling pulseaudio but it did not work, advice?

---

### Post by phillipi on 2009-01-10
To add to this problem, I just recently installed Skype and my sound has stopped working.  It works for Skype but not for anything else.  Here is my info

[I]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I]

everything is turned on in alsamixer.  Alsamixer says my card and chip are PulseAudio 

My sound is still gone after a reboot. Going to "Sound Preferences" I received this error message when attempting to play the test sound:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.*

---

### Post by acmariner99 on 2009-01-10
I meant -- I have no audio playback with skype2.0 and ubuntu8.10

---

### Post by phillipi on 2009-01-10
so you actually lost your ubuntu sound too?

---

### Post by acmariner99 on 2009-01-10
sound with everything else works just fine. Just skype does not work-- actually the problem lies in outgoing sound. The microphone does not work and skype options cause "audio playback" error.

---

### Post by phillipi on 2009-01-10
I discovered something, my sound in Skype is still working perfectly normal, but my regular sound isn't gone.  It's just incredibly quiet.  My volume is turned all the way up on on the speakers, on gnome, and alsamixer.  Any ideas?

---

### Post by acmariner99 on 2009-01-10
try the solution posed here

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by phillipi on 2009-01-10
That link only has a few ideas on how to fix Skype's sound problems (and they are a bit dated).  Sound is fine on Skype, but ever since I installed it sound is very quiet on everything else, so quiet I cant hear it unless I put my ear against the speaker.  I re-installed ALSA and PulseAudio hoping that might help but there was no change.

---

### Post by Username33333 on 2009-01-10
More help with graphics cards and fixing issues.
[http://s5.bite-fight.us/c.php?uid=141327](http://s5.bite-fight.us/c.php?uid=141327)

---

### Post by phillipi on 2009-01-10
Fixed! [http://ubuntuforums.org/showthread.php?t=792836](http://ubuntuforums.org/showthread.php?t=792836)

---

### Post by phillipi on 2009-01-10
acmariner did you try changing the output device in Options>Sound Devices on Skype?  That worked for me when I first installed Skype, it was set to AutoDetect and I switched to Intel HDA or something similar

---

### Post by realtimexxx on 2009-06-01
Changing the output devices using the Skype drop down worked for me, but it was still too quiet. I just solved a quiet sound problem with Ubuntu that I have had for some time.  Maybe it will help someone.  I am no Linux expert but the problem was that the sound was quiet in spite of the fact that it looked like the volume was set at max.  I opened the alsa mixer and some of the settings were not set at max, so I set them all at max.  It is much louder.

---

