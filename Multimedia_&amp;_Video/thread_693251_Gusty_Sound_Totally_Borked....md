---
title: "Gusty Sound Totally Borked..."
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by promet on 2008-02-10
Hi,

My sound system is not working. I was installing and experimenting with some Text to Speech stuff last night (Orca, Speech Dispatcher, Flite, etc.); finally got it to work, and drifted of to sleep to the dulcet tones of robot voice.

Sadly, when I woke up, all sound was "broken". In some cases (Linux version of Realplayer) I am able to get  some sound output as root, via gksudo.  But  none for users.

This is Gutsy, the sound device is Nvidia Nforce AC97 onboard (Realtek), and here are some system/sound details that may be useful:

```

ALSA Audio Debug v0.1.0 - Sun Feb 10 21:05:26 EST 2008
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux prometx.homelinux.org 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_mpu401             10152  0 
snd_mpu401_uart         9984  1 snd_mpu401
snd_seq_dummy           5124  0 
snd_seq_oss            35712  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_intel8x0           35612  4 
snd_ac97_codec        101284  1 snd_intel8x0
snd_seq                54640  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            44800  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                81156  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24580  3 snd_seq,snd_pcm
snd                    56708  19 snd_mpu401,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         11272  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
alias char-major-116    snd

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Feb 10 2008 for kernel 2.6.22-14-generic (SMP).
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650F at irq 17
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 18: [ 0- 2]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 40: [ 1- 0]: raw midi
cat: /proc/asound/hwdep: No such file or directory
00-02: Intel ICH - IEC958 : NVidia nForce2 - IEC958 : playback 1
00-01: Intel ICH - MIC ADC : NVidia nForce2 - MIC ADC : capture 1
00-00: Intel ICH : NVidia nForce2 : playback 1 : capture 1
Client info
  cur  clients : 4
  peak clients : 4
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
Client  20 : "MPU-401 UART" [Kernel]
  Port   0 : "MPU-401 UART MIDI" (RWeX)

Dev Snd ---------------------------------------------------
controlC0  midiC1D0  pcmC0D0p  pcmC0D2p  timer
controlC1  pcmC0D0c  pcmC0D1c  seq

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) XP 2200+
cpu MHz         : 1804.103

RAM -------------------------------------------------------
MemTotal:      1035636 kB
SwapTotal:     1028152 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

```Also, and this may be irrelevant, I can here the Ubuntu sound when my Login screen pops up, i suppose the is some "rootish" function, but zilch for user inside GDM.

Oh, and also, my user IS apart of the "audio" group. Any help would be fab. Thanks!

Promet

---

### Post by promet on 2008-02-10
Hey, didn't notice recent post on same issue just below. Following that tack

[HTML]http://ubuntuforums.org/showthread.php?t=582825[/HTML]

---

### Post by promet on 2008-02-10
The aforementioned thread, aside from providing a very reassuring method for rebuilding the Alsa driver. Did not actually solve my issue.

This may seem rather random, but this is how I solvedmy issue.

I removed my existing .asoundrc file from my home directory (this file overrides the system wide file found at /etc/asound.conf).

I replaced this file with a more robust customized .asoundrc that I found in another forum. Here are the contents of that file:

```

# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### Currently set w/digital-hw as the default output,
### comment out this entire section to use unmixed
### analog as your default
### -jarod
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
#  slave.pcm "dmix-digital"
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
#  - This will accept audio input--regardless of rate--and
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
#  - This will accept audio input--regardless of rate--and
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
#  - This will accept audio input--regardless of rate--and
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

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
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
 device 0
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

```I then opened a terminal and stopped  and started the alsa driver:

```

sudo /etc/init.d/alsasound stop

```
```

sudo /etc/init.d/alsasound start

```

and that got my sound back on. I wish I was skilled enough to explain the precise dynamics of this, but alas, I am not.

Hopefully this will help someone out,

Good luck, and good hunting,
promet

---

