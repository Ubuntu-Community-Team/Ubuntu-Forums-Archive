---
title: "sound cuts or loop constantly"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by vonsko on 2007-01-10
hi my problem is little more than i wrote in a topic but certainly this issues are similiar to them

first of all:
**what's going on: **
[LIST]
[*]when I start system, it hangs, when gnome starts loading, exactly when first sound start play (login success beep or something) when i "killall esd" system start in a few secs
[*]another problem is lot of sound (gaim and others which I already turnd off) - however if they start beeping or something they change to never-ending-loop - it's really annoying (for example while playing music in xmms)
[*]last problem is sound in xmms mplayer , hm and thats all - i think - players that can only play music - you might say right from this step "you must change alsa to oss or oss to esd or esd to alsa or to default... no - this's not an answer - it's not working - eventually it hangs player" - so how it looks?: while playing music it cut about few milisecs and moving after it
[/LIST]

iam searching all over wiki (polish forums, polish channel) and don't know what to do
here is what i've got:
**part of dmesg**
```
[17179588.184000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[17179588.184000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179588.184000] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 11
[17179588.752000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179588.792000] ts: Compaq touchscreen protocol output
[17179588.808000] NET: Registered protocol family 17
[17179588.936000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179589.272000] uhci_hcd 0000:00:10.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17179589.388000] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[17179589.440000] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[17179589.440000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[17179589.440000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179589.440000] PCI: Setting latency timer of device 0000:00:11.5 to 64
```

**part of lspci**
```
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80) 

```
**aplay -l **
```
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: V8237 [VIA 8237], urz&#261;dzenie 0: VIA 8237 [VIA 8237]
  Urz&#261;dzenia podrz&#281;dne: 3/4
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
  Urz&#261;dzenie podrz&#281;dne #1: subdevice #1
  Urz&#261;dzenie podrz&#281;dne #2: subdevice #2
  Urz&#261;dzenie podrz&#281;dne #3: subdevice #3
karta 0: V8237 [VIA 8237], urz&#261;dzenie 1: VIA 8237 [VIA 8237]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
```

I've done for example alsa reinstall from this [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

**mplayer** give me something like this:

```
bin-foley_room-zencd121-advance-2007-fa/01-amon_tobin-bloodstone-fa.mp3
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 3400+ (Family: 15, Model: 79, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Creating config file: /root/.mplayer/config

Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /home/wsen/Download/music/_ninja_tune/Amon Tobin ( 10 )/amon_tobin-foley_room-zencd121-advance-2007-fa/01-amon_tobin-bloodstone-fa.mp3.
Audio file file format detected.
Clip info:
 Title: Bloodstone
 Artist: Amon Tobin
 Album: Foley Room
 Year: 2007
 Comment:
 Track: 1
 Genre: Electronic
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
alsa-init: using device default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video

A: 250.0 (04:10.0) of 257.0 (04:17.0)  2.4%
[b]alsa-lib: pcm_hw.c:600:(snd_pcm_hw_drain) SNDRV_PCM_IOCTL_DRAIN failed: Input/output error
alsa-uninit: pcm closed[/b]

Exiting... (End of file) 
```

i know my english is not as perfect to describe problem as should be
anyway
thanks for any help

---

### Post by vonsko on 2007-01-10
hi
it seems that i found an answer here

[http://alsa.opensrc.org/Via8233#DXS_channels](http://alsa.opensrc.org/Via8233#DXS_channels)

but it's described for diff distros also for some old kernel and alsa - but problem and chipset is exactly the same

---

