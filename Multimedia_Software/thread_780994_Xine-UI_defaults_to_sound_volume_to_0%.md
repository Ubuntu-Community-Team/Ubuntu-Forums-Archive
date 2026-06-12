---
title: "Xine-UI defaults to sound volume to 0%"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Mr. Sunshine on 2008-05-03
I'm running Hardy AMD64.

Xine-UI is my favorite video player, but the version included in Hardy starts up with the sound volume at 0%. Not muted, just at 0%. This is very annoying since I have to put the volume back at 100% every time I open a video.

I didn't have this problem with Gutsy. It always started at 80% (in order to avoid distortion)

I'd like to make it start at 100%, but I can't, even after fiddling with the audio options. How can I fix it?

---

### Post by zir0n on 2008-05-05
I'm having the same problem, xine-ui with gutsy worked fine, but after i installed Hardy, the volume resets to 0 everytime i open it. I have already fiddled around with startup volume setting in the config file located in ~/.xine/config and also manipulating it through the GUI settings as well as the Restore Volume level at start up setting. I'm going to try to compile from source later tonight to see if its just the package version messing up.

---

### Post by gulper_eel on 2008-05-17
I'm having the same problem in Hardy 8.04 x86.  Xine gui defaults to zero volume at launch.  Any ideas?

---

### Post by zir0n on 2008-05-17
I've put a bug report on Launchpad, hopefully this issue gets resolved. No luck in compiling from source. I run into a problem in the .configure part. Ubuntu's libxine package is named libxine1 and messes with the .configure because its looking for libxine, not libxine1. Still trying to fix it messing with the PKG_CONFIG_PATH environment variable. here is the bug link

[https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/231507]("https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/231507")

---

### Post by zir0n on 2008-05-22
It seems to be working fine now, perhaps a new update fixed the problem...

---

### Post by zir0n on 2008-05-26
Actually its not fixed yet... It's acting very weird, sometimes the volume setting will be to what I put in the xine config file and sometimes its at 0%. Its very random. I will try to see why its only doing it sometimes.

---

### Post by zir0n on 2008-07-14
A user named Oliver Joos over at [launchpad bugs]("https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/231507") found that if u modify this string in your "~/.xine/config" using your favorite text editor it will fix the problem.

```
#audio.pulseaudio_device:
```

to

```
audio.pulseaudio_device:pulseaudio
```

---

### Post by mlord on 2010-08-08
If, like me, you've already nuked pulseaudio from your system, then xine needs to be told to use ALSA for playback.

So.. in ~/.xine/config set it as follows:

   **audio.driver:alsa**

Works for me!

---

### Post by adamf663 on 2011-04-15
For me, I had to set gui.audio_mixer_method:Software, then manually
set the xine playback stream to halfway.  Hopefully phonon/pulseaudio
will remember.

---

### Post by bugritall on 2012-08-20
Using the config settings below, xine always starts up with volume at 30:

> # startup audio volume
# [0..100], default: 50
audio.volume.mixer_volume:30

# restore volume level at startup
# bool, default: 0
audio.volume.remember_volume:1


It still doesn't remember my previous volume setting, however.

---

