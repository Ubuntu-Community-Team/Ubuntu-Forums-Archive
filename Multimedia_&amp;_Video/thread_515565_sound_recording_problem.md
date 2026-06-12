---
title: "sound recording problem"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by grooverider on 2007-08-02
hi there ppl,
I got ubuntu feisty, onboard via soundcard, another soundcard, and also a 8t878 hauppauge tv tuner card, i want to capture from my tv card, but somehow i can't get audio to work, I have the line-out of my tv tuner card in the line-in of my onboard via soundcard, i can hear audio while watching tv, and capture also used to work, but i haven'tt used it iin a while and now it does not work, here is some info about my sound conf:

**cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

**cat /proc/asound/pcm**
01-01: Bt87x Analog : Bt87x Analog : capture 1
01-00: Bt87x Digital : Bt87x Digital : capture 1
00-02: CMI8738-MC6 : C-Media PCI IEC958 : playback 1 : capture 1
00-01: CMI8738-MC6 : C-Media PCI 2nd DAC : playback 1
00-00: CMI8738-MC6 : C-Media PCI DAC/ADC : playback 1 : capture 1
02-01: VIA 8233-Pre : VIA 8233-Pre : playback 1 : capture 1
02-00: VIA 8233-Pre : VIA 8233-Pre : playback 4 : capture 1

amixer -c 1 cget name='Capture Source'
numid=3,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'TV Tuner'
  ; Item #1 'FM'
  ; Item #2 'Mic/Line'
  : values=0

**lspci:**
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 10)

**cat /proc/asound/devices**
  2:        : timer
  3:        : sequencer
  4: [ 1- 1]: digital audio capture
  5: [ 1- 0]: digital audio capture
  6: [ 1]   : control
  7: [ 0- 0]: raw midi
  8: [ 0- 2]: digital audio playback
  9: [ 0- 2]: digital audio capture
 10: [ 0- 1]: digital audio playback
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0- 0]: hardware dependent
 14: [ 0]   : control
 15: [ 2- 1]: digital audio playback
 16: [ 2- 1]: digital audio capture
 17: [ 2- 0]: digital audio playback
 18: [ 2- 0]: digital audio capture
 19: [ 2]   : control

**cat /proc/asound/modules**
 0 snd_cmipci
 1 snd_bt87x
 2 snd_via82xx

**cat /proc/asound/oss/devices **
  0: [0- 0]: mixer
  1:       : sequencer
  2: [0- 0]: raw midi
  3: [0- 0]: digital audio
  4: [0- 0]: digital audio
  8:       : sequencer
  9: [0- 0]: raw midi
 10: [0- 0]: hardware dependent
 12: [0- 1]: digital audio
 16: [1- 0]: mixer
 19: [1- 0]: digital audio
 20: [1- 0]: digital audio
 28: [1- 1]: digital audio
 32: [2- 0]: mixer
 35: [2- 0]: digital audio
 36: [2- 0]: digital audio
 44: [2- 1]: digital audio

**cat /proc/asound/oss/sndstat **
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux webchilla 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
C-Media PCI CMI8738-MC6 (model 55) at 0xe400, irq 17
Brooktree Bt878 at 0xdddff000, irq 18
VIA 8233-Pre with ALC200,200P at 0xe000, irq 5

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)
1: Bt87x Digital
2: VIA 8233-Pre (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: MPU-401 MIDI 0-0

Timers:
31: system timer

Mixers:
0: CMedia PCI
1: Bt87x
2: Realtek ALC200,200P rev 0

**cat /proc/asound/pcm**
01-01: Bt87x Analog : Bt87x Analog : capture 1
01-00: Bt87x Digital : Bt87x Digital : capture 1
00-02: CMI8738-MC6 : C-Media PCI IEC958 : playback 1 : capture 1
00-01: CMI8738-MC6 : C-Media PCI 2nd DAC : playback 1
00-00: CMI8738-MC6 : C-Media PCI DAC/ADC : playback 1 : capture 1
02-01: VIA 8233-Pre : VIA 8233-Pre : playback 1 : capture 1
02-00: VIA 8233-Pre : VIA 8233-Pre : playback 4 : capture 1

**cat /proc/asound/seq/drivers **
snd-seq-midi,loaded,1
snd-seq-oss,loaded,0
snd-opl3-synth,empty,1

** cat /proc/asound/timers**
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-2-0: PCM playback 0-2-0 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P1-0-1: PCM capture 1-0-1 : SLAVE
P1-1-1: PCM capture 1-1-1 : SLAVE
P2-0-0: PCM playback 2-0-0 : SLAVE
P2-0-1: PCM capture 2-0-1 : SLAVE
P2-0-2: PCM playback 2-0-2 : SLAVE
P2-0-4: PCM playback 2-0-4 : SLAVE
P2-0-6: PCM playback 2-0-6 : SLAVE
P2-1-0: PCM playback 2-1-0 : SLAVE
P2-1-1: PCM capture 2-1-1 : SLAVE

i don't know how to get it working, also I would like to know how my sounds devices and my tv tuner card are called in the form of '/dev/XYZ' i know my tvcad (the video part) is on /dev/video0 so much is for sure, i also know that mostly sound is on /dev/dsp, but this is not for sure on my system is there a command which gives me a list of my devices int he form of '/dev/XYZ' so i will know for sure? and how the hell do i get to capture the sound from my tv tuner, i don't care if i have to capture it directly from the bt878 or from the line in of one of my soundcards, i have treid lots of things without success, i have also tried this [http://www.linux.org/docs/ldp/howto/BTTV/recording.html](http://www.linux.org/docs/ldp/howto/BTTV/recording.html)
thx for any help :)

---

### Post by variona on 2007-08-09
Check if in your mixer settings are set for capturing from line in.
HTH
variona

---

