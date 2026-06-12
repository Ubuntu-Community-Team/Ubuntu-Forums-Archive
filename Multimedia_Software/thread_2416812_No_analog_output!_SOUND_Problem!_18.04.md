---
title: "No analog output! SOUND Problem! 18.04"
date: 2019-04-15
forum: Multimedia Software
---

### Post by fynneyfoofoo on 2019-04-15
Hey there, I've recently installed Ubuntu 18.04 from a usb, fully  erasing my old chromeos system, and cannot seem to get my sound working,  I've tried for the last two days straight, super frustrated and have  exhausted all my options, would appreciate someone's opinion as I have  no clue haha
HDMI/ Display outputs showing, Dummy output also. 

```
Diagnostic material below---->>
**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**pacmd list-cards**
1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd112c000 irq 124"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d70"
        device.product.name = "Sunrise Point-LP HD Audio"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: no)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: no)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: no)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: no)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: no)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: no)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: no)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: no)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: no)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5200, available: no)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 100, available: no)
        output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 100, available: no)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Output (priority 5200, available: no)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Output (priority 100, available: no)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Output (priority 100, available: no)
        off: Off (priority 0, available: unknown)
    active profile: <output:hdmi-stereo>
    sinks:
        alsa_output.pci-0000_00_1f.3.hdmi-stereo/#0: Built-in Audio Digital Stereo (HDMI)
    sources:
        alsa_output.pci-0000_00_1f.3.hdmi-stereo.monitor/#0: Monitor of Built-in Audio Digital Stereo (HDMI)
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"

[B]pacmd list-sinks
[/B]1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_00_1f.3.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9030
    volume: front-left: 72905 / 111% / 2.78 dB,   front-right: 72905 / 111% / 2.78 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_1f.3>
    module: 7
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd112c000 irq 124"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d70"
        device.product.name = "Sunrise Point-LP HD Audio"
        device.form_factor = "internal"
        device.string = "hdmi:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Intel Skylake HDMI"
        alsa.components = "HDA:80862809,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
[B]
cat /etc/modprobe.d/alsa-base.conf 
[/B]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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
options snd-hda-intel model=auto**iecset audio on**
Mode: consumer
Data: audio
Rate: 44100 Hz
Copyright: permitted
Emphasis: none
Category: general
Original: 1st generation
Clock: 1000 ppm

**lsmod|grep snd**
snd_hda_codec_hdmi     49152  1
snd_soc_skl           102400  0
snd_soc_skl_ipc        61440  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_acpi           16384  1 snd_soc_skl
snd_hda_intel          40960  3
snd_hda_codec         126976  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           81920  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,  snd_hda_codec,snd_soc_skl
snd_hwdep              20480  1 snd_hda_codec
snd_soc_max98357a      16384  0
snd_soc_nau8825        53248  0
snd_seq_midi           16384  0
snd_soc_core          229376  3 snd_soc_max98357a,snd_soc_skl,snd_soc_nau8825
snd_seq_midi_event     16384  1 snd_seq_midi
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_rawmidi            32768  1 snd_seq_midi
snd_pcm                98304  9  snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,   snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_cor   e,snd_soc_nau8825,snd_pcm_dmaengine
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  17  snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwde   p,snd_hda_intel,snd_hda_codec,snd_timer,snd_compre   ss,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
```

---

### Post by wildmanne39 on 2019-04-15
Hello and welcome to the forum!

*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by fynneyfoofoo on 2019-04-16
thanks!

---

### Post by fynneyfoofoo on 2019-04-16
bump*

---

### Post by nik.charles on 2019-05-07
> [B]cat /etc/modprobe.d/alsa-base.conf 

[/B]options snd-hda-intel model=auto**iecset audio on**


looks like error here may have caused problem with snd-hda-intel driver needed for analog audio

```
sudo sed -i 's/model=autoiecset audio on/model=auto/g' /etc/modprobe.d/alsa-base.conf
```

to change it to 'options snd-hda-intel model=auto'

---

