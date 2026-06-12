---
title: "Sound Recording problem"
date: 2008-07-26
forum: Multimedia Software
---

### Post by PJofT35 on 2008-07-26
Hello,
I am having difficulties recording sound in Audacity (sound recorder doesn't work, either).  I have gone into volume control and made sure that there was no x on the mic symbol, and I have fiddled around with the Audacity preferences and selected each different input in turn, and no matter what select Audacity won't start recording, it will just say to check input settings and sample rate.  I know my mic works; I've tried it in windows.  It is plugged in through the microphone hole in the front of my laptop.  Does anyone have ideas on how to fix this?

Thank you for your time and helpfulness.

---

### Post by markbuntu on 2008-07-26
You should have a "capture" slider in the mixer. That is what controls the volume for recording.

---

### Post by PJofT35 on 2008-07-26
Yes, I did that beforehand.  The "capture" slider was fully up, and still it didn't work.  Any other suggestions?  It still said to change the input settings (which I tried, etc.)

Thank you for your time, though!

---

### Post by markbuntu on 2008-07-26
I System/Preferences/Sound, what is Audio Conferencing capture set for?

---

### Post by PJofT35 on 2008-07-26
> **markbuntu said:**
> I System/Preferences/Sound, what is Audio Conferencing capture set for?
Sound playback: Autodetect
Sound capture: STAC92xx Analog

Default Mixer Tracks-
Device: HDA ATI SB (Alsa mixer)

---

### Post by PJofT35 on 2008-07-27
[S]Well, now at least Audacity is working.  Thanks for that, I really don't know what fixed it, but now it works.[/S]

Still Sound Recorder, and, more importantly, Ardour is not working.  When I try to make a new session in Ardour, it says "Ardour could not start JACK.  Either you requested unsupported Audio parameters, or JACK is running as a different user." I made sure that no other sound recording program was running, and I set, under Device, the driver to ALSA and Interface to STAC92xx Analog.  I don't know much about using Ardour, as I haven't been able to start it, but do you (or anyone else) know what is the problem in this case?  Or, should I just stick with Audacity and be grateful that that works?

**Gah, I spoke too soon.  Audacity was working brilliantly, and now it doesn't work anymore!!  The settings never changed, the only thing I did was open and close Ardour.  Now Audacity doesn't work again...Any ideas?**

Thank you very much for your time and effort.

---

### Post by markbuntu on 2008-07-27
jack is probably running. You have to kill it. This is a problem with jack, it does not always close when the application that used it closes so you must kill jack manually. It takes over the sound card and will not let any other app use it.

You can do this with the system monitor or with jack control, which you really should have if you are going to use jack at all, like with ardour. You would not go too wrong if you got all the jack apps, jack control, jack eq, patchage and found a jack tutorial somewhere before you get too far into it.

---

### Post by PJofT35 on 2008-07-27
It wasn't running (according to the system monitor) and audacity still did not work.  I did install JACK control and jackeq, and I sort of fiddled around with jack control, and Audacity still did not work, so I don't think it was because jack was running.

---

### Post by markbuntu on 2008-07-29
You can also use the Pulse Audio Manager to help you figure out what is going on with your sound. If it does not appear in the PAM Device section as 

# something 

then it is using ALSA directly. This causes conflicts. You can get the 

asoundconf.gtk

with Synaptic and then choose PulesAudio in System/Preferences/Default Sound Card and then change the System/Preferences/Sound to ALSA.

There are some serious issues with jack and anything else. I am trying to figure out how to get jack to play nice with everybody else but so far, I have not had much luck.

---

### Post by PJofT35 on 2008-07-30
Huh.  I got asoundconf-gtk, but the only choice was "sb".  Then I installed pulse audio manager (paman), but "sb" was still the only choice.  I ran Audacity and tried to record with the driver set as "alsa-default" for capture, and it still didn't work.  In case it helps, here is what the terminal said from the point when I started Audacity to the point where I tried to record:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... -|hw:0,0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
**Here is where I started to try to record:**
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1034
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1191
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1407
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1983

Does any of this mean anything?

---

### Post by markbuntu on 2008-07-30
That is weird, maybe alsa is messed up, have you tried removing the alsa packages and reinstalling them?

---

### Post by PJofT35 on 2008-07-30
I used Synaptic Package Manager and marked all packages relating to "ALSA" for re-installation and then restarted my computer.  Is there any other work around?

---

