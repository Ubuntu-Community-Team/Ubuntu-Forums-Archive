---
title: "[SOLVED] ATI Radeons audio device taking over the sound"
date: 2008-10-06
forum: Multimedia Software
---

### Post by der_hede on 2008-10-06
I want to use my plain onboard sound but after plugging in a newer AMD/Ati Radeon graphics card the sound does not work anymore. The simple reason is:
For HDMI sound the radeon is a sound device beside being a graphics card.
lspci output:
```
02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
```
Now this device unfortunately gets the first device while the onboard sound gets the second one.
cat /proc/asound/cards:
```
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbeec000 irq 25
 1 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfbffc000 irq 17
```
And because the first device is the standard/default device, every app uses the ati card and not the onboard device. In Gnome you can change this within the audio setup. Other Apps are possibly more complex.

Because my onboard sound and the ATI both are HDA-Intel devices, I cannot blacklist the Atis driver/module without loosing the onboard sound too.

The simplest solution I found is to add the following line to /etc/modprobe.d/alsa-base:
```
options snd_hda_intel index=1,0
```
This reverts the order of the two devices so the onboard sound comes first.

If your onboard sound does not need the snd_hda_intel module, you can simply blacklist snd_hda_intel to disable the Ati HDMI sound, if you don't need it.

For better finding this solution I add some error messages I got:

mplayer:
```
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: No such file or directory
[AO_ALSA] alsa-lib: pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: No such file or directory
```

UrbanTerror and other games using SDL
```
------ Initializing Sound ------
Initializing SDL audio driver...
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
SDL audio driver is "(UNKNOWN)".
SDL_OpenAudio() failed: No available audio device
Sound initialization failed.
```

---

### Post by Yellow Pasque on 2008-10-06
```
asoundconf list
asoundconf set-default-card <name of your onboard card from the list command>
```

---

### Post by der_hede on 2008-10-07
> **Temüjin said:**
> ```
asoundconf list
asoundconf set-default-card <name of your onboard card from the list command>
```

This is a per-user configuration, the module-option thing is system wide.

Second, this method affects the pcm device only. The default midi, time and hwdep devices will still be using the other card. I do not know how to change this with asoundconf, but manually editing .asoundrc.asoundconf is easy.

For a system wide alsa-lib configuration edit the corresponding defaults.* entries in /usr/share/alsa/alsa.conf. As far as the man page states, this will be possibly accessible by asoundconf in the future, too.

---

