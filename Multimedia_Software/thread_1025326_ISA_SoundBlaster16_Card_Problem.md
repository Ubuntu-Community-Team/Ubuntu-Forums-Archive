---
title: "ISA SoundBlaster16 Card Problem"
date: 2008-12-30
forum: Multimedia Software
---

### Post by Kakalto on 2008-12-30
**Ubuntu 8.10**, fresh install (Previously used 7.04)

**Problem:** Sound does not work from GUI.

**Hardware:** ISA SoundBlaster Sound Card (snd-sb16 alsa driver)

**Details:** When ubuntu boots to the login screen, the sound goes off to say that the login screen is ready for me to log in.

As soon as I log in, sound fails. The task tray icon says "No volume control gstreamer plugin and/or devices found." 

From System->Preferences->Sound, I have no default mixer. After clicking "test", I get the following boxes come up when I switch to; 
**Pulseaudio:** ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
``` (Sound preferences then crashes)
**ALSA:** ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: could not get/set settings from/on resource
```.
**OSS:** ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.You don't have permission to open the device.
```

From the console, I cannot access volume controls in alsamixer without specifying "alsamixer -c 0" at which point it gives me volume controls. 

How can I fix all this, get the system to recognise my sound card and 'just work' ?

EDIT: Something referred to in this thread fixed the problem - Atleast to the extent of using OSS as sound system. I couldn't get either Pulseaudio or ALSA to work.

---

### Post by kostkon on 2008-12-30
what happens if you give
```
sudo modprobe snd-sb16
```

---

### Post by Kakalto on 2008-12-30
The module loads, and I can proceed to change mixer volumes through "alsamixer -c 0".

Using straight "alsamixer" without parameters gives:
```
No mixer elems found
```

I get garbled sound when issuing the command
```
$ cat /dev/urandom >> /dev/dsp
```

It seems almost like my sound card is not configured as the default sound card even though it is the only one. Then gstreamer/pulseaudio/whatever gnome tools cannot find it.

Of interest:
```
x@y-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...
x@y-desktop:~$ sudo su
root@y-desktop:/home/x# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: S16 [Sound Blaster 16], device 0: SB16 DSP [DSP v4.13]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Furthermore, I did try adding
```
snd-sb16
```
to /etc/modules and rebooted. This did not fix the problem.

I also added
```
options snd-sb16 index=0
```
to /etc/modprobe.d/alsa-base, to no avail.

---

### Post by pgmer6809 on 2008-12-30
I just read  Klaus Knopper's column in a Linux Format Mag.
In it he says that the newer Ubuntu's use UDEV to automatically detect hardware and then create devices under the /dev.
Thus it may be that UDEV is not detecting such an old sound card and so never creates the device for it.
see if you have /dev/dsp existing. If not try loading your snd-sb16 module manually from the cmd line. Then check for /dev/dsp
Udev should have run and created the device if all is working OK.

If the above works you just have to figure out how to make the snd-sb16 module load at boot time all the time. 
I think there is a way of doing this by adding a parameter to the GRUB menu entry but I am not sure. Maybe others can say.
pgmer6809

---

### Post by Kakalto on 2008-12-30
/dev/dsp exists. I load the module on startup and things still don't work quite how they are expected to.

When I open alsamixer, it won't let me in. I must specifically specify card 0 for it to let me change mixer volumes.

It's like things just aren't picking up on the existence of this card.

More info:
```
x@y-desktop:/home/x$ /usr/bin/speaker-test

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error
```

---

### Post by kostkon on 2008-12-30
> **Kakalto said:**
> Of interest:
```
x@y-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...
x@y-desktop:~$ sudo su
root@y-desktop:/home/x# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: S16 [Sound Blaster 16], device 0: SB16 DSP [DSP v4.13]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Hmmm, it seems that you have the only root can play audio problem. Try to add yourself to the *audio* group (or whatever is called). You can easily do it in *System &#8594; Administration &#8594; Users & Groups*. Then logout and login again to see if that will make a difference.

---

### Post by Kakalto on 2008-12-30
I just updated some packages that I thought may relate to the problem by running the following command, and the problem is fixed:

```
$ sudo apt-get install linux-image-generic alsa-utils libpulse0 libpulsecore5 pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils
```

I don't know exactly what fixed the problem, but it's fixed, and that's the main thing.

EDIT: Just saw your post, I did add myself to the 'audio' group earlier, and I might not have logged out until my recent reboot, this might have been part of the problem.

Thanks anyways, guys.

---

### Post by kostkon on 2008-12-30
Now that your sound works, then I'll give you this tip:
in 8.10 sound is controlled by *PulseAudio* thus, you could set your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect* and then install the *PulseAudio Device Chooser* utility to control your sound.

If you want more info about this, don't hesitate to ask.

---

### Post by Kakalto on 2008-12-30
Pulseaudio and ALSA Options in the sound preferences still don't work, but OSS now worksw and two mixers now show up at the bottom of the dialog: CTL1745 (OSS Mixer) and Sound Blaster 16 (Alsa Mixer). As I said, only OSS works, so I set it to that.

When clicking "test" after setting to pulse or alsa, I still get the same results as above.

---

### Post by kostkon on 2008-12-30
> **Kakalto said:**
> Pulseaudio and ALSA Options in the sound preferences still don't work, but OSS now worksw and two mixers now show up at the bottom of the dialog: CTL1745 (OSS Mixer) and Sound Blaster 16 (Alsa Mixer). As I said, only OSS works, so I set it to that.

When clicking "test" after setting to pulse or alsa, I still get the same results as above.
Since all the sound passes through *PulseAudio* these tests are irrelevant and they don't mean anything anymore.

They will be removed and the whole sound preferences will be reworked since there is the move of a bigger integration of *PulseAudio* in the *Gnome* desktop. For more info about the sound preferences changes, check [here]("https://fedoraproject.org/wiki/Features/VolumeControl").

And the sound preference work only for *GStreamer* anyway. That's why I recommended you to select *Autodetect* (or *PulseAudio*, the same) to be absolutely sure that the various*GStreamer* based apps will use *PulseAudio*.

---

### Post by Kakalto on 2008-12-30
> **kostkon said:**
> Since all the sound passes through *PulseAudio* these tests are irrelevant and they don't mean anything anymore.

They will be removed and the whole sound preferences will be reworked since there is the move of a bigger integration of *PulseAudio* in the *Gnome* desktop. For more info about the sound preferences changes, check [here]("https://fedoraproject.org/wiki/Features/VolumeControl").

And the sound preference work only for *GStreamer* anyway. That's why I recommended you to select *Autodetect* (or *PulseAudio*, the same) to be absolutely sure that the various*GStreamer* based apps will use *PulseAudio*.

My experiences show contrary. Nothing Pulseaudio-related appears to work. I installed *PulseAudio Device Chooser* and it couldn't find any devices. As I said, **Setting to pulseaudio makes sound fail**, and same with ALSA.

Obviously, sound can't always go through Pulseaudio - In this hardware configuration, software tends to crash when Pulseaudio is the set option, sound just doesn't work with ALSA, but things work okay with OSS. (Although sadly I understand there is no software mixing with OSS)

To test this, I changed the settings. When all settings were set to "Pulseaudio", the test failed - and crashed the sound preferences window. When I run Rhythmbox and try to play an mp3, rhythmbox also crashes. 

When all settings are ALSA, the test fails, no crash. Rhythmbox fails to play the mp3.

When all settings are OSS, audio plays. The test works fine, I can play mp3s in rhythmbox.

---

