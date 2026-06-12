---
title: "djplay and jack issue"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by amonsul on 2006-12-23
Hi all!

i've found a new Dj-Mixer-console here: [http://djplay.sourceforge.net/]("http://djplay.sourceforge.net/")


But when i try to install the ubuntu package (Version 0.4.1) i get the following error:

> amonsul@amonsul:~$ djplay
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
No Hercules DJ Console found
Could not get Jack client



someone could help me to solve this problem?

---

### Post by amonsul on 2006-12-23
Maybe i have a Problem with alsa OR???

Look here:

> amonsul@amonsul:~/djplay$   jackd -d alsa
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
amonsul@amonsul:~/djplay$ 


---

### Post by Adri2000 on 2007-06-08
You should try with oss instead of alsa, as stated in /usr/share/doc/djplay/README.Debian.

---

### Post by Sebastral on 2007-06-12
Same here. No luck with oss too.

[INDENT]$ jackd -d oss
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
OSS: failed to open device /dev/dsp: oss_driver.c@526, errno=16
cannot start driver
no message buffer overruns[/INDENT]

---

### Post by Sebastral on 2007-06-13
Well, I did;

$: alsamixer -c0 (= onboard soundcard)
$: alsamixer -c1 (= nothing)
$: alsamixer -c2 (= hercules dj console)
$: cat /proc/asound/seq/*
[INDENT]Client info
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
Client  24 : "DJ Console (WE)" [Kernel]
  Port   0 : "DJ Console (WE) MIDI 1" (RWeX)
snd-seq-midi,loaded,2
snd-seq-oss,loaded,0
OSS sequencer emulation version 0.1.8
ALSA client number 15
ALSA receiver port 0

Number of applications: 0

Number of synth devices: 0

Number of MIDI devices: 3

midi 0: [Midi Through Port-0] ALSA port 14:0
  capability read/write / opened none

midi 1: [MPU-401 UART MIDI] ALSA port 20:0
  capability read/write / opened none

midi 2: [DJ Console (WE) MIDI 1] ALSA port 24:0
  capability read/write / opened none[/INDENT]

$: jackd -d alsa 
[indent]jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback[/indent]
$: qjackctl
$: djplay
[INDENT]Hercules Console found at libusb:003:002 (0x06f8-0xb000)
Successfully attached DJ Console
Port alsa_pcm:capture_1
Port alsa_pcm:capture_2
Port alsa_pcm:playback_1
Port alsa_pcm:playback_2
Port alsa_pcm:playback_3
Port alsa_pcm:playback_4
Port alsa_pcm:playback_5
Port alsa_pcm:playback_6
Audio player cannot su to root
Audio player cannot su to root
[/INDENT]
So djplay starts but still doesn't produce actual sound on speakers :(. See [How getting the Hercules DJ Console to work? ](http://ubuntuforums.org/showthread.php?t=204524)

---

### Post by guitard00d on 2007-07-27
I got djplay to play music just fine, it's just a matter of clicking on the "setup" button on the crossfader window and assigning the djplay ports to the appropriate Jack ports. However, there's a problem with the functionality of the package in the Ubuntu repos. The channel EQ sliders for high/mid/low don't appear. Doesn't matter if I use OSS or Alsa, only the labels for those controls appear on the screen.

Also, doesn't matter if I use OSS or Alsa, the thing still glitches it's playback if you do anything to take the focus away from the djplay application or minimize any of its windows. Tried it with the generic kernel as well as the low latency kernel, makes no difference.

Are there any other viable alternatives to djplay? It looks nice on the screen, and has just the right features needed for a working DJ. But, sadly, the program just isn't ready for prime-time.

---

