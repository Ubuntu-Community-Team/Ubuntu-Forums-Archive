---
title: "Audigy 1 [SB0090] Digital Out problem"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by traxtermaster on 2007-08-02
I've been trying to get my degital output for about 3 weeks now and the only sound i can get is if i play a DVD with AC3 passtrough from "totem movie player" if I disable the optical out from the alsamixer i will get dound from my headphones nut nothing from my Logitech X5500 speakers wich are ProLogic, Dolby Digital and DTS.

aplay -l command returned

```

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
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
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and from an other forum they suggested this ".asoundrc"

```

# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below. If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### Currently set w/digital-hw as the default output,
### comment out this entire section to use unmixed
### analog as your default
### -jarod
pcm.!default {
type plug
## Uncomment the following to use mixed analog by default
# slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
# slave.pcm "dmix-digital"
}
# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
type plug
slave.pcm "analog-hw"
}
# Control device (mixer, etc.) for the Audigy card
ctl.analog {
type hw
card 0
}
# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
# - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
type plug
slave.pcm "dmix-analog"
}
# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
type hw
card 0
}
# Alias for (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
# - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
type plug
slave.pcm "digital-hw"
}
# Control device (mixer, etc.) for the Audigy card
ctl.digital {
type hw
card 0
}
# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
# - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
type plug
slave.pcm "dmix-digital"
}
# Control device (mixer, etc.) for the Audigy card
ctl.mixed-digital {
type hw
card 0
}
# The following devices are not useful by themselves. They
# require specific rates, channels, and formats. Therefore,
# you probably do not want to use them directly. Instead use
# of of the devices defined above.
# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
type hw
card 0
# The default value for device is 0, so no need to specify
}
# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
type hw
card 0
}
# Alias for digital (S/PDIF) output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
type hw
card 0
# device 0
device 2
}
# Control device (mixer, etc.) for the Audigy card
ctl.digital-hw {
type hw
card 0
}
# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-analog {
type dmix
ipc_key 1234
slave {
pcm "analog-hw"
period_time 0
period_size 1024
buffer_size 4096
rate 48000
}
}
# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
type hw
card 0
}
# Direct software mixing plugin for digital (S/PDIF) output
# on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-digital {
type dmix
ipc_key 1235
slave {
pcm "digital-hw"
period_time 0
period_size 1024
buffer_size 4096
rate 48000
}
}
# Control device (mixer, etc.) for the Audigy card
ctl.dmix-digital {
type hw
card 0
}

```

---

### Post by traxtermaster on 2007-08-02
this is the ./aadebug script

```

ALSA Audio Debug v0.1.0 - Thu Aug  2 07:52:07 EDT 2007
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux jason-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_rtctimer            4384  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  3 snd_emu10k1_synth
snd_ac97_codec         98464  1 snd_emu10k1
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_rtctimer,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x531102) at 0xdf40, irq 17
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: raw midi
  6: [ 0- 0]: raw midi
  7: [ 0- 3]: digital audio playback
  8: [ 0- 2]: digital audio playback
  9: [ 0- 2]: digital audio capture
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control
 14: [ 0- 2]: hardware dependent
 15: [ 0- 2]: raw midi
 16: [ 0- 3]: raw midi
00-00: EMU10K1 (FX8010)
00-02: Emux WaveTable
00-03: emu10k1 : Multichannel Playback : playback 1
00-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
00-01: emu10k1 mic : Mic Capture : capture 1
00-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1
Client info
  cur  clients : 5
  peak clients : 5
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
  Output pool :
    Pool size          : 1024
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
Client  16 : "Audigy 1 [SB0090]" [Kernel]
  Port   0 : "Audigy MPU-401 (UART)" (RWeX)
  Port  32 : "Audigy MPU-401 #2" (RWeX)
Client  17 : "Emu10k1 WaveTable" [Kernel]
  Port   0 : "Emu10k1 Port 0" (-We-)
  Port   1 : "Emu10k1 Port 1" (-We-)
  Port   2 : "Emu10k1 Port 2" (-We-)
  Port   3 : "Emu10k1 Port 3" (-We-)

Dev Snd ---------------------------------------------------
controlC0  hwC0D0  hwC0D2  midiC0D0  midiC0D1  midiC0D2  midiC0D3  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2c  pcmC0D2p  pcmC0D3p  seq  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 2998.777
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 2998.777

RAM -------------------------------------------------------
MemTotal:      1035464 kB
SwapTotal:     3028212 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
02:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)

```

---

### Post by lobner on 2007-08-02
I have the same problem. It worked somewhat in the beginning with feisty. But latest updates have somehow changed something, and now it's gone numb.

Been working around a bit with the different sound output units on the system, but no luck.

Would really appreciate a solution.

---

### Post by traxtermaster on 2007-08-02
yeah mine worked for a day tough...

it works great in analog with the headphones but i wish to use the 100% of my sound system

---

### Post by traxtermaster on 2007-08-04
Is this a big mistery....:confused:

---

### Post by cheeesemonger on 2007-08-15
Lobner probably tried this already, but does JACK handle it any better? A lot of people at ALSA (for some reason beyond me) don't recommend the default daemon, apparently. I hate to sound like a rabid ALSA-hater, but you might even want to try OSS. That might hurt some of your software though... :-(

I have one of these lying around, so once I put it in my box again I'll try to fiddle with it.

---

