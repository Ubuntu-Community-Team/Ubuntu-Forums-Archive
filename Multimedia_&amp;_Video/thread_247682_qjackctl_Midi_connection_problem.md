---
title: "qjackctl Midi connection problem"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by emmpopo on 2006-08-31
I am trying to connect my external keyboard to rosegarden.
I think I have all the usual suspects set-up, but...

I can't make a connection in qjackctl between the 64:MPU-401 output (left) to the rosegarden (right) (or actually anything. I have also tried ZynAddSubfx).

I can't either make a connection the other way around, from rosegarden to 64:MPU-401 input (keyboard).

Help...

---

### Post by dolson on 2006-08-31
That is weird... What happens? The connection lines don't get drawn? You could try an alternate, like Patchage, perhaps?

---

### Post by emmpopo on 2006-08-31
tqjackctl tries to draw it, but then disappears immediately.

Since then, I have tried the same in rosegarden, by ticking the midi record device 64:0 MPU-401 tick box, but noticed a SoundDriver error message, complaining that it can't use this record device.

---

### Post by dolson on 2006-08-31
What is SoundDriver?

Do you have the snd-seq module loaded, per the wiki?

---

### Post by emmpopo on 2006-09-01
It was not SoundDriver, but AlsaDriver. :redface:  This is the output of rosegarden when I try to tick the Manage Midi Devices>64:0 MPU-0401 MIDI 0-0 record device tick box:

"...
AlsaDriver::setRecordDevice - 64:0 failed to subscribe device 1 as record port
..."

Let me give you a bit more info on my system ;) :

my sound card: C-Media PCI

lsmod | grep snd

snd_rtctimer            3340  0
snd_seq_dummy           3844  2
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  22 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_cmipci             34336  5
gameport               15496  1 snd_cmipci
snd_opl3_lib           10624  1 snd_cmipci
snd_hwdep               9376  1 snd_opl3_lib
snd_mpu401_uart         7808  1 snd_cmipci
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_opl3_lib,snd_rawmidi
rtc                    13492  1 snd_rtctimer
snd_bt87x              14664  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  5 snd_cmipci,snd_bt87x,snd_pcm_oss
snd_timer              25220  4 snd_rtctimer,snd_seq,snd_opl3_lib,snd_pcm
snd_page_alloc         10632  2 snd_bt87x,snd_pcm
snd                    55268  23 snd_seq_oss,snd_seq,snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd

cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux piano 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738 (model 37) at 0xe800, irq 7
Brooktree Bt878 at 0xd8001000, irq 10

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)
1: Bt87x Digital

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: MPU-401 MIDI 0-0

Timers:
7: system timer

Mixers:
0: CMedia PCI
1: Bt87x

 cat /proc/modules | grep midi
snd_seq_midi 9376 0 - Live 0xe4af9000
snd_seq_midi_event 7552 2 snd_seq_oss,snd_seq_midi, Live 0xe4af6000
snd_seq 51984 22 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xe4b5f000
snd_rawmidi 25504 2 snd_seq_midi,snd_mpu401_uart, Live 0xe4a90000
snd_seq_device 8716 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_opl3_lib,snd_rawmidi, Live 0xe4a4a000
snd 55268 24 snd_seq_oss,snd_seq,snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xe4991000

cat /proc/asound/seq/clients
Client info
  cur  clients : 8
  peak clients : 8
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 63:0, 129:0, 131:0
Client  62 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
    Connecting To: 131:0
    Connected From: 131:1
Client  63 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
Client  64 : "MPU-401 MIDI 0-0" [Kernel]
  Port   0 : "MPU-401 MIDI 0-0" (RWeX)
Client 128 : "Virtual Keyboard" [User]
  Port   0 : "Virtual Keyboard" (R-e-)
    Connecting To: 130:0, 131:0
  Output pool :
    Pool size          : 500
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
Client 129 : "Client-129" [User]
  Port   0 : "qjackctl" (-W--)
    Connected From: 0:1
  Input pool :
    Pool size          : 200
    Cells in use       : 0
    Peak cells in use  : 2
    Alloc success      : 14
    Alloc failures     : 0
Client 130 : "ZynAddSubFX" [User]
  Port   0 : "ZynAddSubFX" (-We-)
    Connected From: 128:0, 131:1
  Input pool :
    Pool size          : 200
    Cells in use       : 0
    Peak cells in use  : 1
    Alloc success      : 88
    Alloc failures     : 0
Client 131 : "Rosegarden" [User]
  Port   0 : "Rosegarden input" (-We-)
    Connected From: 0:1, 128:0, 62:0
  Port   1 : "Rosegarden output" (r-e-)
    Connecting To: 130:0, 62:0
  Output pool :
    Pool size          : 2000
    Cells in use       : 0
    Peak cells in use  : 1
    Alloc success      : 105
    Alloc failures     : 0
  Input pool :
    Pool size          : 2000
    Cells in use       : 0
    Peak cells in use  : 2
    Alloc success      : 2
    Alloc failures     : 0

cat /proc/asound/devices
  8: [0- 0]: raw midi
 18: [0- 2]: digital audio playback
 26: [0- 2]: digital audio capture
 17: [0- 1]: digital audio playback
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
 57: [1- 1]: digital audio capture
 56: [1- 0]: digital audio capture
 32: [1- 0]: ctl

 cat /proc/asound/modules
0 snd_cmipci
1 snd_bt87x

Am I missing a snd_mpu401 here???

cat /proc/asound/card0/midi0
MPU-401 MIDI 0-0

Output 0
  Tx bytes     : 0
Input 0
  Rx bytes     : 0

---

### Post by emmpopo on 2006-09-07
Could there be a conflict between the Midi port/driver and the Game  port/driver? Do I have to disable the Game driver? :confused:

---

### Post by dolson on 2006-09-08
Can you run amidi -l and paste the output here?

---

### Post by emmpopo on 2006-09-11
amidi -l

Device   Name
hw:0,0   MPU-401 MIDI0-0

also, I did a 

amidi -d

ALSA lib rawmidi_hw.c:231: (snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: Input/output error

is this helping???

---

### Post by emmpopo on 2006-09-21
do I need to change my sound card? which one would you recommend?

---

### Post by dolson on 2006-09-22
Sorry for the late response.. But your problem is more advanced than I am.

If you're in the market for an expensive, pro card, I'm the wrong person to ask having no experience with anything really great.

If you just want something that does the job, I use an Audigy2 ZS and a SB Live! 5.1 in each of my PCs. MIDI works fine on both.

---

### Post by furanku on 2006-12-14
Hi!

Greetings from the gentoo site of the world ;)

I have exactly the same problem on my AMD64 x2 system with an "Genius Sound Maker Value 5.1" (C-Media Electronics Inc CM8738 (rev 10) based) sound card. I bought the card just as a cheap midi interface :/

I already posted on the alsa mailing list and on the gentoo forums:

[http://forums.gentoo.org/viewtopic-t-524397-highlight-.html](http://forums.gentoo.org/viewtopic-t-524397-highlight-.html)

Until now I found no solution nor did I get any helpful hints, did you proceed any futher? If I find a solution I'll reply here.

---

