---
title: "Bad playback with odd sounds in Ubuntu 9.04 Jaunty"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Taterade on 2009-09-03
I have Ubuntu 9.04 installed on a Dell Latitude Cpi laptop. The sound card is a Neomagic NM256ZX. The problem is that whenever i playback sound it skipped and you could also here another noise like it was being controlled by something else at the same time.
All options in the Preferences>Sound have this problem except for the OSS- open Sound System options, under all three playback tests. But outside the tests the sound is still chopped and has a weird noise coming through. After poking(bad idea on my part) around in the Volume Control, it appears that multiple sound servers all have an effect on the card and whether or not it plays. It also now plays back a strange noise with no trace of the song or video I tried to playback should sound like. I considered removing pulseaudio as I'm sure that is part of the problem, but I did not want to remove Ubuntu-desktop as i want to still get the updates.

---

### Post by mrgnash on 2009-09-04
OpenSound is an excellent cure for such problems, and if you've already considered replacing Pulseaudio, I recommend following [these instructions](https://help.ubuntu.com/community/OpenSound) :)

---

### Post by Taterade on 2009-09-05
After following the instructions on the OpenSound page the sound returned to how it had acted after fresh install(playing the sound + a odd noise), however ALSA still had control over sound for reasons that escape me so I followed the instructions at[SIZE=1] [/SIZE][SIZE=1]Configure ALSA Apps to Use OSS (OPTIONAL)[/SIZE] on the OpenSound page. This failed to work and also caused my /dev/dsp file to disappear. Ubuntu still recognizes that my sound card is there in lspci -v bt both the Volume control and Sound prefrences don't recognize that i have a sound card.
aplay -l returns
aplay: device_list:217: no soundcards found...

lspci -v (other components not copied)
01:00.1 Multimedia audio controller: Neomagic Corporation NM2360 [MagicMedia 256ZX Audio]
    Subsystem: Dell Device 008b
    Flags: medium devsel, IRQ 5
    Memory at f9800000 (32-bit, prefetchable) [disabled] [size=8M]
    Memory at fda00000 (32-bit, non-prefetchable) [disabled] [size=1M]
    Capabilities: <access denied>
    Kernel modules: snd-nm256

If I can get the volume control to recgonize my card again, I can deal woth the noise because it may just be my soundcard.

---

