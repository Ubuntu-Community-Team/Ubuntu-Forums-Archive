---
title: "No sound from Ubuntu 8.10 or 9.04 with NVidia nForce 2 card"
date: 2009-04-18
forum: Multimedia Software
---

### Post by AndrooUK on 2009-04-18
I have tried and tried to find out how to get the ALSA/PulseAudio working on my Ubuntu 8.10 (fresh installation).

OSS works, but it sounds rubbish and does not work with anything else running.

I've tried [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and numerous other Ubuntu forum postings, to no avail.

Maybe I've missed something, I'm not sure.

*aplay -l* in the terminal gives:

```
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [Unknown]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The sound modules appear to be installed after using the command *find /lib/modules/`uname -r` | grep snd* in the terminal.

*lspci -v | less* in the terminal gives (amongst other items):

```
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing 
Unit (rev a2)
        Subsystem: ABIT Computer Corp. Device 1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Contr
oler (MCP) (rev a1)
        Subsystem: ABIT Computer Corp. Device 1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=128]
        Memory at e0081000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

```

and:

```
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Device 1008
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 9000 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

```

although the Audigy card is not used, and not really wanted right now.  The motherboard is Abit NF7-S V2.0.  According to the Alsa project website, the card is an AC97 product ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia")).

I was wondering if anyone had any ideas or experienced similar problems?

In the sound settings, I've tried everything (Autodetect, ALSA, OSS, and PulseAudio).  Only OSS works.  I've tried following forums for advice, but it seems only to get the sound card to show up to the computer.  The sound card definitely works fine, because it has been used under Windows XP.

If anyone requires further information, please ask.

Thank you very much in advance for any assistance, for I am getting very despondent!  :cry:

Andrew.

---

### Post by tofiluk on 2009-04-18
> **AndrooUK said:**
> I have tried and tried to find out how to get the ALSA/PulseAudio working on my Ubuntu 8.10 (fresh installation).

OSS works, but it sounds rubbish and does not work with anything else running.

I've tried [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and numerous other Ubuntu forum postings, to no avail.

Maybe I've missed something, I'm not sure.

*aplay -l* in the terminal gives:

```
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [Unknown]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The sound modules appear to be installed after using the command *find /lib/modules/`uname -r` | grep snd* in the terminal.

*lspci -v | less* in the terminal gives (amongst other items):

```
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing 
Unit (rev a2)
        Subsystem: ABIT Computer Corp. Device 1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Contr
oler (MCP) (rev a1)
        Subsystem: ABIT Computer Corp. Device 1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=128]
        Memory at e0081000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

```

and:

```
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Device 1008
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 9000 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

```

although the Audigy card is not used, and not really wanted right now.  The motherboard is Abit NF7-S V2.0.  According to the Alsa project website, the card is an AC97 product ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia")).

I was wondering if anyone had any ideas or experienced similar problems?

In the sound settings, I've tried everything (Autodetect, ALSA, OSS, and PulseAudio).  Only OSS works.  I've tried following forums for advice, but it seems only to get the sound card to show up to the computer.  The sound card definitely works fine, because it has been used under Windows XP.

If anyone requires further information, please ask.

Thank you very much in advance for any assistance, for I am getting very despondent!  :cry:

Andrew.

it may sound foolish for me to ask but have you tried the volume control? i also happen to had a similar problem but only to find out that the volume is not set to its maximum.

---

### Post by AndrooUK on 2009-04-18
Yes the volume is all the way up, when not in OSS mode the computer speaker beeps when it has a notification or similar.

I had the problem of no volume when I first installed 8.04.  :D

(That is, 8.04 on my laptop!)

---

### Post by markbuntu on 2009-04-19
What does aplay -l have to say?

---

### Post by Motw on 2009-04-20
Im not really sure what youve done, but Ive experienced a similar program and the thing that helped for me is disabling the onboard soundcard.

So if you havent tried that; restart get in your CMOS and disable it ;)

---

### Post by AndrooUK on 2009-04-20
Hey thanks for your input everyone, someone suggested to me disabling the unwanted Audigy card but I didn't know how to do that.  I physically removed the sound card and now the nForce2 card works beautifully!

Does Ubuntu have a problem with conflicting hardware in general?

Anyway, solved!  ;)

---

