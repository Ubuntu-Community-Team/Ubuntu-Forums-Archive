---
title: "No sound after loading last recommended updates"
date: 2009-07-28
forum: Multimedia Software
---

### Post by luangwa on 2009-07-28
Attempts tried to track down "no sound problem"
I'm exasperated! I have been trying for 6 days to figure out why I have no sound after loading the last recommended updates. I am running Ubuntu 9.04 on a Dell 8250 with a Sound Blaster Live card. 

I tried the following as per [http://ubuntuforums.org/showthread.php?t=1219650](http://ubuntuforums.org/showthread.php?t=1219650) in hopes that it would pin point the problem but since I am a newbie all of this is doesn't make any sense. I am showing it in hopes that someone who is has a working knowledge of Ubuntu 9.04  might help in diagnosing my problem. My Sound Blaster Live card is listed in OSS4. I have double checked to make certain that the mute isn't on and that the volumes are at 100%.

I would appreciate any assistance in correcting this problem.

Here are the most resent attempts to track down the trouble.
 
1.  ~$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0

2. ~$ lspci -v 
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04) 
	Subsystem: Dell Device 0145 
	Flags: bus master, fast devsel, latency 0 
	Memory at e8000000 (32-bit, prefetchable) [size=128M] 
	Capabilities: <access denied> 
	Kernel driver in use: agpgart-intel 
	Kernel modules: intel-agp 

00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04) 
	Flags: bus master, 66MHz, fast devsel, latency 64 
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64 
	Memory behind bridge: fc000000-fdffffff 
	Prefetchable memory behind bridge: f0000000-f7ffffff 
	Kernel modules: shpchp 

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64 
	I/O behind bridge: 0000e000-0000efff 
	Memory behind bridge: fe100000-fe2fffff 
	Kernel modules: shpchp 

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04) 
	Flags: bus master, medium devsel, latency 0 
	Kernel modules: iTCO_wdt, intel-rng 

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04) (prog-if 80 [Master]) 
	Subsystem: Dell Device 0145 
	Flags: bus master, medium devsel, latency 0 
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8] 
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1] 
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8] 
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1] 
	I/O ports at ffa0 [size=16] 
	Kernel driver in use: ata_piix 

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04) 
	Subsystem: Dell Device 0145 
	Flags: medium devsel, IRQ 11 
	I/O ports at dcf0 [size=16] 
	Kernel modules: i2c-i801 

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) 
	Subsystem: nVidia Corporation Device 015a 
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16 
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M] 
	Memory at f4000000 (32-bit, prefetchable) [size=64M] 
	Memory at f3f80000 (32-bit, prefetchable) [size=512K] 
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K] 
	Capabilities: <access denied> 
	Kernel driver in use: nvidia 
	Kernel modules: nvidia, nvidiafb, rivafb 

02:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
	Subsystem: First International Computer, Inc. Device 1234 
	Flags: bus master, medium devsel, latency 64, IRQ 19 
	I/O ports at ece0 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 

02:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
	Subsystem: First International Computer, Inc. Device 1234 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	I/O ports at ecc0 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 

02:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20) 
	Subsystem: First International Computer, Inc. Device 1234 
	Flags: bus master, medium devsel, latency 64, IRQ 16 
	Memory at fe1ffc00 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 
	Kernel driver in use: ehci_hcd 

02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
	Subsystem: First International Computer, Inc. Device 1234 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	I/O ports at eca0 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 

02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
	Subsystem: First International Computer, Inc. Device 1234 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	I/O ports at ec80 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 

02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20) 
	Subsystem: First International Computer, Inc. Device 1234 
	Flags: bus master, medium devsel, latency 64, IRQ 19 
	Memory at fe1ff800 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 
	Kernel driver in use: ehci_hcd 

02:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X 
	Subsystem: Creative Labs Device 1003 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	I/O ports at ec60 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: EMU10K1X 
	Kernel modules: snd-emu10k1x 
 
02:09.1 Input device controller: Creative Labs [SB Live! Value] Input device controller 
	Subsystem: Creative Labs Device 1003 
	Flags: bus master, medium devsel, latency 64 
	I/O ports at ec58 [size=8] 
	Capabilities: <access denied> 
	Kernel driver in use: Emu10k1_gameport 
	Kernel modules: emu10k1-gp 

02:0a.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02) 
	Subsystem: 3Com Corp, Modem Division Device 00aa 
	Flags: medium devsel, IRQ 19 
	I/O ports at ec50 [size=8] 
	Capabilities: <access denied> 
	Kernel driver in use: serial 

02:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10) 
	Subsystem: Dell Device 0145 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	Memory at fe1fe000 (32-bit, non-prefetchable) [size=4K] 
	I/O ports at ec00 [size=64] 
	Memory at fe1c0000 (32-bit, non-prefetchable) [size=128K] 
	Capabilities: <access denied> 
	Kernel driver in use: e100 
	Kernel modules: e100, eepro100 

3. ~$ lsmod | grep snd 
snd_emu10k1x           23812  3 
snd_ac97_codec        112292  1 snd_emu10k1x 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  3 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_emu10k1x,snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    62628  17 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
ac97_bus                9856  1 snd_ac97_codec 
snd_page_alloc         16904  2 snd_emu10k1x,snd_pcm 

4.~$ sudo modprobe snd-intel8x0  ( nothing was displayed)
5.$ cvlc 1.wav  
VLC media player 0.9.9a Grishenko 
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team 
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 
[00000001] main libvlc debug: translation test: code is "C" 
[00000404] dummy interface: using the dummy interface module...
Then nothing else happened. The cursor just floats at the bottom of the window as though it were processing..... nothing....no sound from the speakers!

6. /$ cat /proc/asound/cards 
 0 [Live           ]: EMU10K1X - Dell Sound Blaster Live! 
                      Dell Sound Blaster Live! at 0xec60 irq 18
7. /$ lsmod | grep oss 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  4 snd_intel8x0,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss 
snd_seq_oss            37760  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    62628  18 snd_intel8x0,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

8. /$ ls -l /dev/dsp* 
crw-rw----+ 1 root audio 14, 3 2009-07-26 13:14 /dev/dsp 

9. /$ cat /proc/asound/cards 
 0 [Live           ]: EMU10K1X - Dell Sound Blaster Live! 
                      Dell Sound Blaster Live! at 0xec60 irq 18 
john@John:/$ lsmod | grep oss 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  4 snd_intel8x0,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss 
snd_seq_oss            37760  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    62628  18 snd_intel8x0,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
john@John:/$ ls -l /dev/dsp* 
crw-rw----+ 1 root audio 14, 3 2009-07-26 13:14 /dev/dsp 
john@John:/$ ls /dev/snd -al 
total 0 
drwxr-xr-x   2 root root     200 2009-07-26 13:14 . 
drwxr-xr-x  17 root root    4540 2009-07-26 13:14 .. 
crw-rw----+  1 root audio 116, 9 2009-07-26 13:14 controlC0 
crw-rw----+  1 root audio 116, 4 2009-07-26 13:14 midiC0D0 
crw-rw----+  1 root audio 116, 8 2009-07-26 13:15 pcmC0D0c 
crw-rw----+  1 root audio 116, 7 2009-07-26 13:25 pcmC0D0p 
crw-rw----+  1 root audio 116, 6 2009-07-26 13:14 pcmC0D1p 
crw-rw----+  1 root audio 116, 5 2009-07-26 13:14 pcmC0D2p 
crw-rw----+  1 root audio 116, 3 2009-07-26 13:14 seq 
crw-rw----+  1 root audio 116, 2 2009-07-26 13:14 timer 

10. /$ groups `whoami` 
john adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare 
I followed : HOWTO: PulseAudio Fixes & System-Wide Equalizer Support
at  [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 
Here are the results:

11. ~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
libasound2-plugins is already the newest version. 
padevchooser is already the newest version. 
libsdl1.2debian-pulseaudio is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 

12. ~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package libflashsupport is not installed, so not removed 
Package flashplugin-nonfree-extrasound is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 

Tried to launch PulseAudio from Application/Sound-Video 
Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Tried to launch manually. 

13. ~$ pulseaudio & pavucontrol 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE. 
I: caps.c: Dropping root privileges. 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE. 
[1] 14144 
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges: 
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits. 
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user. 
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz. 
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz. 
E: socket-server.c: bind(): Address already in use 
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed. 
E: main.c: Module load failed. 
E: main.c: Failed to initialize daemon. 

(pavucontrol:14146): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed 

(pavucontrol:14146): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed 
[1]+  Exit 1 

Did I miss any test to pin point the probem? Or should I take a course on lip reading to find out the news? Or is there a way to remove the last updates? May be the sound will return?????

---

### Post by igorzwx on 2009-07-28
If your hardware is supported by OSS4,
I may try to help to install it.

My recommendation:

1. Install another Ubuntu 9.04 in dual boot (for experiments)

2. Install OSS4 following this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

you may need this info too:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)

Try to be carefull!!!

---

### Post by luangwa on 2009-08-13
Problem Solved

---

### Post by Alfiegerner on 2009-08-26
Can you tell us your solution?  I'm struggling with sound issues myself.

---

### Post by eden.gc on 2010-03-30
Hi there,

Can you share your solution, I am having the same issue?

---

