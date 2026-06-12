---
title: "Surround sound from SBLive 5.1"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by zdotz on 2007-01-14
I am trying to set up surround sound from my SBLive 5.1 via the digital output to my Sony receiver. As it is now I can hear any file I play but only in a stereo format even if it is a surround sound wave file or a surround sound movie.

Here is some important information about my system;

Ubuntu Edgy
SBLive 5.1 w/digital out
Alsa drivers and utilities version 1.0.13
lspci -v reports:
```
05:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 32, IRQ 66
        I/O ports at b000 [size=32]
        Capabilities: [dc] Power Management version 1

05:07.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at b400 [size=8]
        Capabilities: [dc] Power Management version 1
```

aplay -l reports:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Results from:
```
speaker-test -D surround51 -c 6
```
produces only noise on the front left and front right channels.

Results from:
```
aplay -Dsurround51 test.wav
``` -a test surround sound file I have.
```
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:909: Channels count non available
```

***EDIT: This also produces loud ticking noises. Sounds like the digital signal itself. ***EDIT

Also adjusting the volume levels, mutes and balances in alsamixer seems to do nothing, at least from what I can hear.

I have consulted the alsa page for my device [http://alsa.opensrc.org/Emu10k1](http://alsa.opensrc.org/Emu10k1) and the Ubuntu Comprehensive Sound Problem Solutions Guide [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) as well as countless other resources but none of those suggestions either apply to me or are helpful to my problem. 

So, my questions to the community are these;
What further configurations do I need to make to get the surround sound to work?
What are the best alsamixer settings for my purpose? (even though it doesn't seem to make an audible difference)
What does the aplay error i get mean and is it of consequence?
Are there any audio player specific configurations I should be making to facilitate the surround sound playback?

Thanks in advance.

---

### Post by Riarheos on 2008-01-16
I've just solved the problem for myself.
Post this into your ~/.asoundrc:

pcm.!default {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.2.2 1
    ttable.3.3 1
    ttable.4.4 1
    ttable.5.5 1
}

---

