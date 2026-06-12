---
title: "module build failed for ATI SBx00 sound card"
date: 2009-01-11
forum: Multimedia Software
---

### Post by pussinboots on 2009-01-11
Originally installed Ubuntu Hardy on my desktop, just upgraded to Intrepid.  Sound doesn't work, not sure if it worked before.  Followed the SoundTroubleshooting instructions ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)).  Here is the output of lspci -v:

[INDENT]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Giga-byte Technology Device a022
        Flags: slow devsel, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Kernel modules: snd-hda-intel[/INDENT]

I determined that my driver is either atiixp, atiixp-modem or hda-intel.  I tried installing (then removing) each with modprobe.  To test, I tried playing an ogg file with ogg123.  Each time, I got:

[INDENT]ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA snd_pcm_hw_params error: Input/output error
Error: Cannot open device alsa.
[/INDENT]

I then tried building my own drivers with the module-assistant.  I separately tried atiixp{,-modem} and hda-intel.  Both times, I got a compilation error:

[INDENT]   CC [M]  /usr/src/modules/alsa-driver/acore/info.o
 /usr/src/modules/alsa-driver/acore/info.c: In function ‘resize_info_buffer’:
 /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit
 declaration of function ‘PAGE_ALIGN’[/INDENT]

Any ideas what else I should try?

Thanks,

Jason

---

### Post by pussinboots on 2009-01-11
Solution was to switch to OSS:

[INDENT][https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)[/INDENT]

Jason

---

