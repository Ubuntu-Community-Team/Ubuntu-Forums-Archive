---
title: "Another victim of sound hardware disappering from pulseaudio  [lucid 10.04 amd64]"
date: 2010-07-21
forum: Multimedia Software
---

### Post by nstenz on 2010-07-21
After re-arranging my desk and moving computers around, my sound hardware no longer appears in the volume mixer applet, and I have no sound.  ALSA sees everything fine.  After messing with it for countless hours, I finally learned how to set autospawn = no on pulseaudio and reload alsa, which works great- but then of course I can't use the default panel mixer applet to adjust volume and configure the different outputs.

Everything worked fine when I first installed lucid from scratch less than 2 weeks ago (this is a brand new box).  The only change I made was switching from an analog CRT to DVI on a flat panel.  The only reason I mention that is when I fired it back up, the HDMI audio out showed up as the only sound card, and I know this board shares the same output for both DVI and HDMI.  I've since disabled HDMI audio in the BIOS while troubleshooting, so now no hardware shows up.

It's the onboard audio of an ASUS M4A89GTD PRO/USB3 motherboard (AMD 850 chipset).
```
$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
```

The codec reports as a Realtek ALC892.
```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC892
```

```
$ cat /proc/asound/card0/pcm0c/info
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC892 Analog
name: ALC892 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 0
```

```
$ hwinfo --sound
17: PCI 14.2: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4383
  Unique ID: 5Dex.YgS6XqJHu+4
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8410 
  Revision: 0x40
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe3f4000-0xfe3f7fff (rw,non-prefetchable)
  IRQ: 16 (3099368 events)
  Module Alias: "pci:v00001002d00004383sv00001043sd00008410bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```


Here's the full log from the alsa-info.sh script:
[http://www.alsa-project.org/db/?f=5029748c091d7978889ea899ad4009a8dee0e510](http://www.alsa-project.org/db/?f=5029748c091d7978889ea899ad4009a8dee0e510)

I have no idea how, but sometime during the time I was messing with it yesterday morning, I got the hardware to show up again as a generic audio device after I installed a backported copy of maverick's kernel (which added full support for the ALC892's channels).  However, later in the day, it wasn't working again (maybe after another reboot).

Can anybody help me figure out what's going on?  I'll save my Pulseaudio = garbage rant for later.

---

### Post by nstenz on 2010-07-23
Continuing to research today after not being able to use digital out even after picking it in the Multimedia Systems Selector app...

I've read several places that support for the ALC892 was added in 2.6.33, but it's not in the current kernel doc-
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

I saw mention of this command as well, which returns nothing for me:
> find /proc/asound/card* -type f | grep codec | xargs grep "^Codec\|^Vendor Id\|^Subsystem Id\|^Revision Id" | grep -B2 -A1 $(lspci -nv | grep -A1 0403 | grep Subsystem | sed 's/://g' | awk '{ print $2 }')

Anybody?

also:
```
$ alsactl init
Unknown hardware: "HDA-Intel" "Realtek ALC892" "HDA:10ec0892,104383c0,00100302" "0x1043" "0x8410"
Hardware is initialized using a guess method
```

I wonder if the backported kernel I'm running doesn't include a backported snd-hda-intel driver?

---

### Post by nstenz on 2010-07-24
One last bit of info- *pulseaudio -vvvv* outputs this:
> D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
**D: module-udev-detect.c: /devices/pci0000:00/0000:00:14.2/sound/card0 is busy: yes**
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #4; argument: "").


Would that cause hardware to not show up at all?  If so, how can I find out what's using it?  *sudo fuser -v /dev/dsp* /dev/snd/** gives me no output.

---

