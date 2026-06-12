---
title: "Pulseaudio &amp; Wine"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by netelemental on 2007-11-10
Hey all, 
I've got pulseaudio installed and working great - it didn't seem like the default sound packages were doing what I wanted, and so I got pulseaudio and have been extremely happy. I can run most applications fine, and a few that don't cooperate will run when I use padsp - except for Wine. Whatever I do, I can't seem to get wine to produce sound, and the one place on the internet that looks like it could help([http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/](http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/)) is missing the vital image that should so the configuration settings. WInecfg is also the only application for which I receive 
```

ERROR: ld.so: object 'libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
ALSA lib ../../../src/control/control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
ERROR: ld.so: object 'libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.

```
in the terminal. Any thoughts?

Thanks,
NetElemental

---

### Post by Mawl on 2007-11-11
Hi, 
first off - this is my 1st post, hello everyone :)

i ran into the same problem yesterday evening. Here's a screenschot of the config the worked for me (yay, finally Warcraft III AND backgroundmusic!)

regards David

---

### Post by netelemental on 2007-11-11
Hey,
Thanks for responding, but nothing so far - I don't seem to have the Pulseaudio Virtual OSS device under my options, and I suspect padsp simply isn't working because of the terminal errors, but I don't know. I attached by configuration as well as the console, would you mind taking a look and letting me know what you think?

Thanks!

---

### Post by Mawl on 2007-11-11
Hi,
I have version 0.97 because pulseaudio wouldn't detect my soundcard on 0.96. Maybe that version has a fix for this issue, too? There is no package yet, so you'll have to compile PA yourself. It's not hard but hunting down all the dependencies is a hassle...
If you choose to compile yourself and you get an error about ltdl missing, install the package libltdl3-dev - the configure-script doesn't check for it for some reason..

I hope this helps

David

---

### Post by oni5115 on 2008-02-19
Are there any instructions for compiling pulse audio?  Unfortunately, the readme that the download of pulse audio 0.9.9 had was simply "For more information see http://pulseaudio.org/", and I didn't see a section on how to compile the source code on the website.

I'd like to get this working with Wine as well, as the whole reason I installed it was to try and make it so I can pump up the sound of Ventrilo, while turning down the sound of Audacity.

I noticed the errors I get are a little different:
> ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:1
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:1
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer


This is with:
ALSA 1.0.14 - ubuntu repos
PulseAudio 0.9.6-1 - ubuntu repos
Wine 0.9.54 (and 0.9.55) - wiineHQ

---

### Post by rapiscan on 2008-02-21
From the OSS Applications section of the Pulse Audio perfect setup:
"To run applications that support the OSS API for audio playback (/dev/dsp) on top of PulseAudio you can use the tool padsp that is part of the PulseAudio distribution."

So if you run 'padsp winecfg', you should have the 'PulseAudio Virtual OSS' device listed.  I'm not sure how to make this permanent (or if you would want to).

See [http://www.pulseaudio.org/wiki/PerfectSetup#OSSApplications](http://www.pulseaudio.org/wiki/PerfectSetup#OSSApplications)

---

### Post by oni5115 on 2008-02-21
Thanks for the reply, oddly enough even without using padsp, I got sound working just fine by selecting ESD instead of ALSA in winecfg.  Didn't need to padsp and use OSS at all.

I still get the above error messages in the terminal, but the sound works just fine.

---

### Post by kebinusan on 2008-03-26
This is a slightly bigger problem on AMD64 as there is no 32 bit asound plugin for pulse audio installed.

---

