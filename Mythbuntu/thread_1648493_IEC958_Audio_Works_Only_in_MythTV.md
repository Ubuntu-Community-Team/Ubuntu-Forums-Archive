---
title: "IEC958 Audio Works Only in MythTV"
date: 2010-12-18
forum: Mythbuntu
---

### Post by Digicrat on 2010-12-18
I'm running a fresh install of Mythbuntu 10.10 with MythTV 0.24.  After restoring the mythtv settings from the previous install, the sound works fine for LiveTV, recordings, and MythMusic.

The problem is, I can't get digital sound to work anywhere outside of myth - ie: Flash (Pandora/Youtube), VLC, etc.  I've checked the sound mixers (alsamixer and the generic mixer on the XFCE menu) but haven't been able to get anywhere (all output sources set to 100%).  Even explicitly choosing the device in VLC (which I've done prior to the reinstall) is not working.

In addition to the digital coaxial connection to my sound system, I also have the standard speaker output connected to a spare input.  The analog sound source does work for all non-Myth applications, while MythTV outputs only to SPDIF.  

MythTV is configured to use ALSA:iec958:CARD=NVidia,DEV=0.  This is the S/PDIF digital output on the motherboard.  

Any suggestions on how to get the rest of the system to use the digital audio device?

Thanks,
- David

---

### Post by iitywygms on 2010-12-19
go here and read up.
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
I would not try the upgrade until you try the suggested fixes.
Specifically.
Before reporting "NO SOUND" problems - check if your alsamixer-channels are activated and unmuted (gnome-mixer/volume-control/preferences)!!
Very often there are headphone-jack, Toslink, SPDIF or microphone issues reported. Usually this has something to do with wrong alsamixer settings or more seldom with a wrong model-id assigned to your sound-driver in /etc/modprobe.d/alsa-base.conf .
If you're lacking certain controls in alsamixer or your driver is not even being loaded, you should check-out your model-id in attached HD-Audio-Models.txt.
I strongly recommend to try similar model-id's matching your codec to checkout if your faulty function gets working.
I'd guess 80% of the reported problems (group: other than alsamixer issues) over here are related to the model setting in alsa-base.

I searched for days and this finally fixed all sound issues for me.
I have no asound.conf or asoundrc and everything works as it should.

I had the same issue as you.  I had to add my model to alsa-base.conf before it would work.

---

### Post by Lem on 2010-12-19
I had the same issue which I solved by installing pulseaudio. Now I have sound in both MythTV and XBMC.

---

### Post by Digicrat on 2010-12-22
After a brief commercial break to deal with some ACPI boot issues, back to the original sound issue.  I've made progress, thanks in part to iitywygms's link, and am posting here primarily as reference for others.  

I have stereo sound working in all applications now, however I suspect that additional (5.1) channels would not work outside of myth if I had a source to test it.  (See the end of this post for my active question on this)



I'm already running Alsa version 1.0.23, probably as a result of enabling the Ubuntu repositories for MythTV 0.24.  

I've tried installing PulseAudio without any positive effect.  With pulseaudio running, I received an error about device in use from the alsa aplay test application.  I resolved that issue by creating a ~/.pulse/default.pa file according to directions on another post for loading the proper alsa module.  The contents of my default.pa file is
```

load-module module-alsa-sink device=hw:0 channels=6 channel_map=front-left, front-right, front-center, rear-left, rear-right, lfe
load-module module-alsa-source device=hw:0

```


To find a list of devices and modes supporting 5.1, I used "aplay -L".  iec958 is the only properly configured device shown, which corresponds to the device being used by the mythfrontend.  The surround entries are configured for the discrete channel outputs on the sound card, which I do not have connected.
```

...
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=NVidia,DEV=0
...
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

Following directions from [http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc), I created an ~/.asoundrc file containing:
```
pcm.!default iec958:NVidia
```


Stereo sound is now working in all applications.
```
speaker-test -D iec958 -c2
```

Testing additional channels (I have a 5.1 setup), however, results in:
```

speaker-test -D iec958 -c6

speaker-test 1.0.23

Playback device is iec958
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

```


My receiver does show that it is receiving a 5.1 channel signal from the mythfrontend.  All other applications transmit only a 2.0/stereo sound (as expected from sources I've tested).  

Does the error from the speaker-test above mean that if I do run some 5.1-enabled application in the future, that it will only work in 2-channel mode?  If so, how can I correct it?

Thanks,
- David

---

