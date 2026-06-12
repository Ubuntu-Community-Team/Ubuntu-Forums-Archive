---
title: "Continuing video and sound problems"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-12-08
I've had problems with video and sound since I've had this PC. I'm moving soon and may be without internet for a while, so I'd love to get at least one of these fixed so I can do more with the PC while it's off-line.

The video problem is one of refresh rates. If I install the restricted NVIDIA drivers, Kubuntu defaults to 43Hz whenever it starts up. I can change it to whatever I like video nvidia-settings, but the default is still 43Hz. The monitor System Settings says the refresh rate range for 1024x768 (the resolution I want to use) is 50-55Hz, xorg.conf says the maximum is 85Hz, using "dpkg-reconfigure xserver-xorg" makes no difference, all accounts are affected, and manually editing xorg.conf makes no difference. The 2D-only nv driver does not have this problem, but applications are starting to complain to me about the lack of hardware accelerated video.

The sound problem is one where I can only use Open Sound System for sound, ALSA doesn't produce anything. This means I can only get sound from one application at any given time, and none at all from Flash. Installing or configuring TiMidty (or using any application that uses it) produces:

```
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
```

Which seems to indicate that ALSA is not configured properly. Can anyone help with getting ALSA working properly?

---

### Post by Rhapsody on 2007-12-08
I've also run [aadebug](http://alsa.opensrc.org/index.php/Aadebug) and these were the results.

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

Since I didn't mention it before, my video card is integrated ('GeForce6-class', that's all I know about it) and my sound card is too (RealTek ALC861VD).

---

