---
title: "Another Sound Doesn't Work... No Other Fixes Seem to Work... Please Assist"
date: 2009-09-14
forum: Multimedia Software
---

### Post by absolute linux noob on 2009-09-14
Hi there, I am very, very new to Linux and Ubuntu - just installed it off a fresh CD last week.

I run a Dell Dimension E521 with an AMD Athlon 64-bit processor. The sound card is a Creative Sound Blaster X-Fi. There is also a nVidia audio device although I don't recall ever having used this when on XP.

I installed Ubuntu 9.04 - Jaunty Jackalope 64 bit Desktop Edition.

From the very beginning sound has not worked in any form. Although through the PulseAudio drivers etc. I can see that there is some kind of output, however, if there is any sound  coming out it's definitely not audible.

I was previously running Windows XP but completely overwrote with Ubuntu, I've seen in places that settings in Windows - ie. if you have it muted in Windows - it overlaps into Ubuntu, however, I imagine having wiped the hard-drive this would not have an effect.

AlsaMixer seems to have never installed correctly in that the command alsamixer gave me this error: "cannot open mixer: No such file or directory" although I do seem able to access the config. however, after selecting my card I still have no luck.

I have installed the soundcard drivers and have also upgraded and re-installed ALSA multiple times, most recently I received many errors when trying to load builds however it didn't elaborate as to what caused these.

ALSA appears to be installed but I suspect it may not work because it is defaulted to mute and I am not able to access the mixer to change this.
I have attempted to use several graphical versions of the ALSA controller and it says it is un-muted but I still don't get sound from anything.

Since having scoured the internet for a fix for ALSA and tried many combinations and failing I tried something else. I tried using PulseAudio and can see that there is a output when selecting it with the sound preferences etc. however, I still didn't have sound. Since messing with it a wee bit I now get the error message when trying to select test with PulseAudio: "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument".

Furthermore, the problem I am encountering with everything is that none of my soundcards are found for the Default Mixer Device. This is obviously a major problem and I don't see how it could have occurred when it was only just clean installed.

Some further data outputs:
> andre@andre-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
> andre@andre-desktop:~$ sudo alsa reload
[sudo] password for andre: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/andre/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
[WARNING IS REPEATED]> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
    Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

04:08.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 1003
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 9c00 [size=32]
    Memory at efc00000 (64-bit, non-prefetchable) [size=2M]
    Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel modules: snd-ctxfi, ctxfiAs stated I'm fairly new to Ubuntu so while I try my best I will probably require comprehensive hand holding beginner steps. Will not hesitate to offer further data if required. It will be greatly appreciated if people can help me find a fix to this seemingly common problem and I thank you in advance for reading this.

---

### Post by absolute linux noob on 2009-09-15
The main problem appears to be that despite having supposedly configured ALSA to my soundcard the Sound Preferences still doesn't detect it in the Default Mixer. How can I remedy this???

---

### Post by absolute linux noob on 2009-09-18
Bump>?

---

