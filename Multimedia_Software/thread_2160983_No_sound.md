---
title: "No sound"
date: 2013-07-09
forum: Multimedia Software
---

### Post by JimS on 2013-07-09
...
NO Sound on my new HP2000 laptop when using Lubuntu 13.04.
Other distros (Windoz, Ubuntu, & Mint) have sound.

Alsa-base and Alsa-utils are installed per Synaptic.

Audacious gives the following error msgs:
ALSA error: No suitable mixer element found.
ALSA error: snd_mixer_find_selem failed.

/usr/share/applications has no alsa or pulse applications.

No sound from speakers.
No sound from headset.

What to do?
...

---

### Post by JimS on 2013-07-09
...
More data.
What do you think?

jim@jim-HP-2000-Notebook-PC:~$ sudo aplay -l
[sudo] password for jim: 
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


jim@jim-HP-2000-Notebook-PC:~$ lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
	Subsystem: Hewlett-Packard Company Device 188b
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port (prog-if 00 [Normal decode])
--
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 188b
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)


jim@jim-HP-2000-Notebook-PC:~$ speaker-test

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory

...

---

### Post by JimS on 2013-07-13
Bye Bye Lubuntu.
This seems a shame that
one should even have
such basic sound issues.
Bad Buntu.

---

### Post by Sergei_Dragunov on 2013-08-29
Hello,

I'm kind of new with Linux in general, I'm trying Lubuntu 13.04. and I also ran into this problem. I've looked at many possible solutions and I've tried most of them that I could to no avail. The details of my computer are:

_**aplay -l**_
[COLOR=#0000cd]***** List of PLAYBACK Hardware Devices *****[/COLOR]
[COLOR=#0000cd]*card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]*[/COLOR]
[COLOR=#0000cd]*  Subdevices: 1/1*[/COLOR]
[COLOR=#0000cd]*  Subdevice #0: subdevice #0*[/COLOR]
[COLOR=#0000cd]*card 1: Generic_1 [HD-Audio Generic], device 0: STAC92xx Analog [STAC92xx Analog]*[/COLOR]
[COLOR=#0000cd]*  Subdevices: 0/1*[/COLOR]
[COLOR=#0000cd]*  Subdevice #0: subdevice #0*[/COLOR]

[U][B]cat /proc/asound/cards
[/B][/U]*[COLOR=#0000cd] 0 [Generic        ]: HDA-Intel - HD-Audio Generic[/COLOR]*
*[COLOR=#0000cd]                      HD-Audio Generic at 0xf0344000 irq 54[/COLOR]*
*[COLOR=#0000cd] 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic[/COLOR]*
*[COLOR=#0000cd]                      HD-Audio Generic at 0xf0340000 irq 16[/COLOR]*

[U][B][FONT=Monaco]cat /proc/asound/card*/codec* | grep Codec
[/FONT][/B][/U]*[COLOR=#0000cd]Codec: ATI R6xx HDMI[/COLOR]*
*[COLOR=#0000cd]Codec: IDT 92HD81B1X5[/COLOR]*

[U][B][FONT=Monaco]cat /proc/asound/modules
[/FONT][/B][/U]*[COLOR=#0000cd] 0 snd_hda_intel[/COLOR]*
*[COLOR=#0000cd] 1 snd_hda_intel[/COLOR]*

_**I've also tried, at sometimes adding these lines into the alsa-base.conf**_
[COLOR=#0000cd]*#options snd_HD-Audio Generic index=0 (I've commented this out because it didn't work)*[/COLOR]
[COLOR=#0000cd]*#options snd_HD-Audio Generic index=1 (I've commented this out because it didn't work)*[/COLOR]
[COLOR=#0000cd]*alias snd-card-0 snd-hda-intel*[/COLOR]
[COLOR=#0000cd]*alias sound-slot-0 snd-hda-intel*[/COLOR]
[I][COLOR=#0000cd]options snd-hda-intel model=auto position_fix=1
[/COLOR]
[/I]I couldn't get the alsa-info.sh so I can't post what its output could have been. My sources were:
[http://forums.debian.net/viewtopic.php?f=16&t=53708](http://forums.debian.net/viewtopic.php?f=16&t=53708)
[http://forums.bodhilinux.com/index.php?/topic/8035-problems-with-sound-solved/](http://forums.bodhilinux.com/index.php?/topic/8035-problems-with-sound-solved/)
[https://bbs.archlinux.org/viewtopic.php?id=133987](https://bbs.archlinux.org/viewtopic.php?id=133987)

But me being new, I couldn't follow much except to execute the commands. Also I'm sorry if I've posted this question on the wrong section, but this is the only result that popped up. I've also installed pulseaudio and pulseaudio-utils, so the errors are no longer there, but the audio's still out.

Thanks for any info you can give.

---

### Post by gordintoronto on 2013-08-29
Sergei, it's always helpful if you provide some description. Is this a laptop or Desktop? Brand and model? Are you using HDMI, and, if so, going to what? You expect sound on earphones/speakers or built-in speakers? What program are you running which should produce sound?

That said, about 80% of the time, no sound is because it's muted or the volume is reduced to zero -- and there are at least three places where sound can be muted or reduced to zero. Start with Sound Settings, which I think is available in Lubuntu.

---

### Post by Sergei_Dragunov on 2013-08-29
@gordintoronto

thanks for the reply. the unit is a laptop, HP Pavilion DV6. i was actually able to make the sound work by going through the steps again, don't know what i missed the first couple of tries (sorry i'm such a dunce :oops:). the only problem now is for the earphones. again thanks for the reply.

---

### Post by Irvin_Yip on 2013-08-30
I also can't get Lubuntu 12.04 work on HDMI sound. I got sound from headset but no sound on HDMI...

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

----------------------------------------------
irvin@irvin-Aspire-R3600:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
irvin@irvin-Aspire-R3600:~$ 

can run on hardware 0,3, but no sound...

:(

---

### Post by Irvin_Yip on 2013-08-30
sudo apt-get install pavucontrol:i386

sudo apt-get install pulseaudio

found in LinuxMint forum!

then u'll got a Pulse Audio Volume Control in your start menu, go to last tab and choose HDMI as output.

SOLVED!!

---

