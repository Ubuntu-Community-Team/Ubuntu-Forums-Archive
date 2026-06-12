---
title: "ALSA not working with ALC861VD"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-12-09
This is a very established problem now. I have a desktop computer with a Realtek ALC861VD (an HDA Intel device) that has an odd problem in that it only works if I use Open Sound System. I appear to get no sound whatsoever if I use ALSA, though the system detects the sound card perfectly well.

alsamixer volume is correct, KMix volume is correct. It definitely appears that my motherboard has six jacks on it, but specifying 'model=6stack-dig' in alsa-base makes no difference.

Using TiMidty results in the following output:

```
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
```

Using aadebug gives the following:

```
ALSA Audio Debug v0.1.0 - Sat Dec  8 16:41:02 GMT 2007
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux chihiro 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_rtctimer            4384  1
snd_hda_intel         263712  3
snd_mpu401              9640  0
snd_mpu401_uart         9600  1 snd_mpu401
snd_pcm_oss            44672  1
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54660  14 snd_hda_intel,snd_mpu401,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdfff8000 irq 16
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: raw midi
  5: [ 1]   : control
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
cat: /proc/asound/hwdep: No such file or directory
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 2
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
Client  20 : "MPU-401 UART" [Kernel]
  Port   0 : "MPU-401 UART MIDI" (RWeX)
Client 128 : "TiMidity" [User]
  Port   0 : "TiMidity port 0" (-We-)
  Port   1 : "TiMidity port 1" (-We-)
  Port   2 : "TiMidity port 2" (-We-)
  Port   3 : "TiMidity port 3" (-We-)
  Output pool :
    Pool size          : 500
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
  Input pool :
    Pool size          : 1000
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0

Dev Snd ---------------------------------------------------
controlC0  controlC1  midiC1D0  pcmC0D0c  pcmC0D0p  seq  timer

CPU -------------------------------------------------------
model name      : AMD Sempron(tm) Processor 2800+
cpu MHz         : 1607.389

RAM -------------------------------------------------------
MemTotal:       450564 kB
SwapTotal:     1975984 kB

Hardware --------------------------------------------------
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

As I said, everything seems to work fine using the OSS compatibility mode, but ALSA would be much nicer to use.

---

### Post by jetpeach on 2008-04-26
so i have the same card, with only three jacks, but never had a problem when using 7.10. i just upgraded to 8.04 though, and cant get sounds working for the life of me.

there are so many threads on this, but the only thing i've really found to try (without success) was editing the asla-base file to add options.. if anyone has help, please suggest! 

  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel


EDIT: wow, so i gave up last night, came back this morning and in 5 minutes of dinging around i figured it out. apparently, sound was actually working is now MUCH quieter than it was previously. basicaly, _every_ volume meter [the relevant ones, that is-mixer,PCM, _and_ front] needed to be nearly all the way up before i got  sound. i still get to a just loud enough volume, but it happens in the last 10% of the volume meters

---

