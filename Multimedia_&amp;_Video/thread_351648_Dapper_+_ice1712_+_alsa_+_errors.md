---
title: "Dapper + ice1712 + alsa + errors"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by Khaz on 2007-02-02
Hi all; wondering if someone could shed some light on this.

I get errors like

ALSA lib pcm_direct.c:815:(snd_pcm_direct_initialize_slave) requested or auto-format is not available

ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to initialize slave

when I open Gedit from the terminal and edit files like /home/.asoundrc

I can't for the life of me figure out how to get this M-Audio Card (Audiophile 2496, ice1712) to work.

Steps I've taken:
1. aplay -l gives output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

2. cat /proc/asound/modules gives:
```
0 snd_intel8x0
1 snd_ice1712
2 snd_mpu401

```

3. I have edited the bottom of my /etc/modprobe.d/alsa-base to look like this:
```

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-ice1712 index=0
options snd-intel8x0 index=-2
options snd-mpu401 index=-2

```
I assume that giving an index of -2 will cancel the loading of those two sound devices (my onboard intel8x0 and midi controller mpu401)

I have tried editing my asound.conf, i have tried editing my .asoundrc, i have tried deleting both files, I have tried with the default files. I cannot get sound to come out of the "Sound Juicer" CD player! I have unmuted all channels in Alsamixer. I have tried using Envy24Control to monitor sound - none of the channels have any visible sound entering/leaving.

My M-Audio card is connected to an external DAC (Logitech Z5500 speakers and receiver) through the SPDIF Coaxial output. I have switched the Alsamixer IEC958/IEC958 controls to "digital" as I guess that those are the digital outputs.

I've spent about 3 days googling/searching/trying and I've seen nothing come out of my hunt. What I gather from the errors I'm getting is that I haven't set a sample rate or somesuch and the auto feature doesn't work? I have no idea of how to test or get a debug so I can't work it out myself.

Thanks,

KZ

---

### Post by Khaz on 2007-02-02
Aright, I got this card to work. I:

1. Reinstalled the alsa-utils, alsa-tools, and all alsa packages from the Synaptic Package Manager.

2. Deleted /etc/asound.conf, removed /home/kyle/.asoundrc, went back to my backup'd /etc/modules.conf and /etc/modules (there are no ALSA entries in them anymore.basically).

3. I did leave the "Default soundcard" fix above in place because I have more than 1 soundcard.

4. All the alsamixer settings were still unmuted and everything. I restarted Gnome with CTRL-ALT-Backspace and poof.

---

