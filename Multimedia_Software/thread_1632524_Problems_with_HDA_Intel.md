---
title: "Problems with HDA Intel"
date: 2010-11-28
forum: Multimedia Software
---

### Post by klemi on 2010-11-28
Hallo,

I have at the moment no sound from the loudspeaker of my laptop of LG.
To the history:

After the installation of 10.04 I had no problems with the sound. I have tried out several programmes - everywhere functioned the sound about the internal speakers.

Then I wanted to enable in a USB port to lead sound to my USB D/A converter and to forward the sound about this then.
However, this went after some efforts about created "/etc/asound.conf" them so looks:
```
pcm.usbdac {
type hw;
card Center;
}
pcm.plugusb {
type plug;
slave.pcm "usbdac";
}
ctl.plugusb {
type hw;
card Center;
}

```

The USB converter in a USB port put - wonderfully functioned.

But after unplug of the external A-D converter the "internal sound did not go sometime" in the laptop suddenly any more.

Then I have installed "asoundconf-gtk" - but this select to the respective audio card did not function anyhow.

Now after some rumprobieren from various "Wikis - sound" folds nothing at all more with regard to Sound.

After some experiments from various "Wikis - sound" functioned generally small sound more.
I also have now under "audio-settings" in the bleed "output" only "dummy output" stand. This was not, admittedly, before in such a way.

```
klemens@klemens-LG-S510:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC262
Codec: LSI ID 1040
Codec: Nvidia MCP77/78 HDMI

```

Reltek ALC263 also stood before always in the menu of the bleed "output" under system-> sound

```
klemens@klemens-LG-S510:/etc$ hwinfo --sound
14: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.e3yXuNoYe3F
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1854 "LG Electronics, Inc."
  SubDevice: pci 0x0130 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfc220000-0xfc223fff (rw,non-prefetchable)
  IRQ: 48 (1317 events)
  Module Alias: "pci:v00008086d0000293Esv00001854sd00000130bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

In "/etc/modprobe.d/alsa-base.conf" I have pasted the last line. Whether this line is right, I do not know.

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto

```

```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

```
```
ALC262
======
  fujitsu       Fujitsu Laptop
  hp-bpc        HP xw4400/6400/8400/9400 laptops
  hp-bpc-d7000  HP BPC D7000
  hp-tc-t5735   HP Thin Client T5735
  hp-rp5700     HP RP5700
  benq          Benq ED8
  benq-t31      Benq T31
  hippo         Hippo (ATI) with jack detection, Sony UX-90s
  hippo_1       Hippo (Benq) with jack detection
  sony-assamd   Sony ASSAMD
  toshiba-s06   Toshiba S06
  toshiba-rx1   Toshiba RX1
  tyan          Tyan Thunder n6650W (S2915-E)
  ultra         Samsung Q1 Ultra Vista model
  lenovo-3000   Lenovo 3000 y410
  nec           NEC Versa S9100
  basic         fixed pin assignment w/o SPDIF
  auto          auto-config reading BIOS (default)

```

With ALSAMIXER I can only see the HDMI-Output and not the Realtek ALC262

Why?

[http://picpaste.de/alsamixer.png]("http://picpaste.de/alsamixer.png")


:frown:I do not look though, to tell the truth, any more.

Who helps me?

---

