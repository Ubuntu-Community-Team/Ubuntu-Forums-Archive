---
title: "Two days ago all sound stopped working"
date: 2008-12-05
forum: Multimedia Software
---

### Post by mrule on 2008-12-05
Two days ago sound stopped working on my machine. All applications which use sound now crash, hang, or run but with no sound output. Sound was working perfectly before that. I am running Ubuntu (2.6.27-10-generic) on a 64 bit machine ( Dell studio slim 540s ). Sound seemed to break after a routine update (but those seem to occur every six hours ago so this is not very enlightening). It also followed the installation of a new video card. So far I have not found a solution on any other thread. Following the instructions on the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") had no effect. 

Things that aren't right : 

Amarok, Rhythmbox become unresponsive when trying to play a file. VLC runs but with no sound output. No systems sounds, no startup sounds, no sounds at all.

system>preferences>sound produces a number of errors :

testing autodetect under "sound events : sound playback" produces : 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

testing ALSA under "sound events : sound playback" produces : 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.

testing OSS under "sound events : sound playback" produces :
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.

testing PulseAudio sound server under "sound events : sound playback" produces :
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
_and the control panel freezes_

testing other individual card features under the same menu returns similar errors.


Things that seem normal :

Hardware seems ok : 
mrule@Petra:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My username is in the audio group, and all audio controls that I can find are turned all the way up, headphone jack is enabled, sound card is enabled in the BIOS, etc...

---

### Post by psyke83 on 2008-12-05
You're completely ignoring PulseAudio, which is now responsible for sound mixing of all applications from Intrepid onwards. The sticky guides in this subforum are outdated in this respect.

Ensure your configuration is correct. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by mrule on 2008-12-05
I have followed the steps on [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578") as suggested. I was unable to get pulseaudio to work and all the same problems persist.

pavucontrol shows no devices available for output, input, recording, or playback

upon launching pulseaudio we see the following (errors?) :
mrule@Petra:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
W: alsa-util.c: Unable to determine current swparams: Operation not permitted
W: module-alsa-sink.c: Got POLLERR from ALSA
W: module-alsa-sink.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): Input/output error
W: alsa-util.c: Unable to determine current swparams: Operation not permitted
W: module-alsa-source.c: Got POLLERR from ALSA
W: module-alsa-source.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): Input/output error

---

### Post by siddharthseth on 2008-12-06
i am guessing that your system loads snd-hda-intel module .. try 
> dmesg | grep hda and see if there is any error in loading that module.

---

### Post by mrule on 2008-12-06
Yes, there seem to be several errors : 

mrule@Petra:~$ dmesg | grep hda 
[   15.558175] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.560508] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   17.564508] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x100f0000
[   18.104899] hda_codec: invalid dep_range_val 0:7fff
[   18.104901] hda_codec: invalid dep_range_val 0:7fff
[   18.104979] hda_codec: invalid dep_range_val 0:7fff
[   18.104980] hda_codec: invalid dep_range_val 0:7fff
[   18.105058] hda_codec: invalid dep_range_val 0:7fff
...

What does this mean ( and why would it stop working suddenly when it seemed happy before ) ?

---

### Post by siddharthseth on 2008-12-06
Mate

I can think of only three possible reasons 
1) You did a kernel update and are no longer using the old "working" sound drivers.
2) There is some problem with your hardware.
3) Your hardware is not "Exactly" supported. In that case sometimes it may work with the drivers that have been loaded, some times not.  

For 1) you can choose to boot into the older kernel version and see if the problem is there. 
For 2) Boot into Windows (if you have it) and see if the soundcard is working.
For 3) Check on ALSA's website. Get and compile the latest code and see if it helps. 

Going by the error u posted above, I feel its a driver issue and hope so for you too.

---

### Post by mrule on 2008-12-10
Well, my specific sound chipset doesn't seem to be supported by ALSA

82801JI (ICH10 Family) HD Audio Controller

I found [this thread]("http://ubuntuforums.org/showthread.php?t=898737"), which seems to indicate it will be virtually impossible to get sound working again. I tried booting into older kernels and running Knoppix, sound still didn't work. I'll switch the machine back to Vista for a bit and hope this gets fixed in soon.

---

