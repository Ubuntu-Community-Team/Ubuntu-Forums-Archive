---
title: "Capture video/audio from USB Terratec Grabster AV350MX - PulseAudio"
date: 2014-03-11
forum: Multimedia Software
---

### Post by frowi on 2014-03-11
Don't know anymore in which direction to go, and need some help.

I am trying to capture videos with subject device, and the video as such is absolutely no problem with v4l2.

But no sound!:mad:

I've read that some do not suggest to use PA at all, rather to stay with pure ALSA.
So I tried with and w/o PA to no avail. At one time, though, (surprise!) I did actually get an audio stereo signal from the PA Grabster volume control and could indeed record the video sound to a file with this command:

```
~$ avconv -f alsa -ac 2 -ar 48000 -f pulse -i alsa_input.usb-0ccd_Grabster_AV_350-01-G350.analog-stereo -acodec libvorbis -aq 6 test.ogg
  
```

however, after having stopped this process I did not managed to repeat this, anymore. PA Grabster volume control does not show any signals anylonger.
In the Meantime I have tried so many settings that I am afraid the ALSA/PA combination needs to be readjusted.

From my system I have the following information:
```
~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: VT1708S Analog [VT1708S Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 3: VT1708S Digital [VT1708S Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```

```
~$ arecord -l
**** Liste der Hardware-Geräte (CAPTURE) ****
Karte 0: Intel [HDA Intel], Gerät 0: VT1708S Analog [VT1708S Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 1: G350 [Grabster AV 350], Gerät 0: USB Audio [USB Audio]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0

```

```
~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 45
 1 [G350           ]: USB-Audio - Grabster AV 350
                      Grabster AV 350 at usb-0000:00:1a.7-6, high speed

```

```
~$ pactl list sources
Quelle #0
        Status: RUNNING
        Name: alsa_input.usb-0ccd_Grabster_AV_350-01-G350.analog-stereo
        Beschreibung: Grabster AV 350 Analog Stereo
        Treiber: module-alsa-card.c
        Sample-Angabe: s16le 2ch 44100Hz
        Kanalzuordnung: front-left,front-right
        Besitzer-Modul: 5
        Stumm: no
        Lautstärke: 0: 100% 1: 100%
                0: 0,00 dB 1: 0,00 dB
                Verteilung 0,00
        Basis-Lautstärke:  54%
                     -16,00 dB
        Sink-Monitor: k. A.
        Latenz: 5007 usec, eingestellt 20000 usec
        Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        Eigenschaften:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "USB Audio"
                alsa.id = "USB Audio"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "1"
                alsa.card_name = "Grabster AV 350"
                alsa.long_card_name = "Grabster AV 350 at usb-0000:00:1a.7-6, high speed"
                alsa.driver_name = "snd_usb_audio"
                device.bus_path = "pci-0000:00:1a.7-usb-0:6:1.1"
                sysfs.path = "/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1/sound/card1"
                udev.id = "usb-0ccd_Grabster_AV_350-01-G350"
                device.bus = "usb"
                device.vendor.id = "0ccd"
                device.vendor.name = "TerraTec Electronic GmbH"
                device.product.id = "0084"
                device.product.name = "Grabster AV 350"
                device.serial = "0ccd_Grabster_AV_350"
                device.string = "front:1"
                device.buffering.buffer_size = "352800"
                device.buffering.fragment_size = "176400"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Grabster AV 350 Analog Stereo"
                alsa.mixer_name = "USB Mixer"
                alsa.components = "USB0ccd:0084"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-usb"
        Profile:
                analog-input-linein: Line In (priority: 8100)
        Aktive Profile: analog-input-linein
        Formate:
                pcm

Quelle #1
        Status: RUNNING
        Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
        Beschreibung: Monitor of Internes Audio Analog Stereo
        Treiber: module-alsa-card.c
        Sample-Angabe: s16le 2ch 44100Hz
        Kanalzuordnung: front-left,front-right
        Besitzer-Modul: 6
        Stumm: no
        Lautstärke: 0: 100% 1: 100%
                0: 0,00 dB 1: 0,00 dB
                Verteilung 0,00
        Basis-Lautstärke: 100%
                     0,00 dB
        Sink-Monitor: alsa_output.pci-0000_00_1b.0.analog-stereo
        Latenz: 0 usec, eingestellt 20000 usec
        Flags: DECIBEL_VOLUME LATENCY 
        Eigenschaften:
                device.description = "Monitor of Internes Audio Analog Stereo"
                device.class = "monitor"
                alsa.card = "0"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xf9ff8000 irq 45"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "3a3e"
                device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "0"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        Formate:
                pcm

Quelle #2
        Status: RUNNING
        Name: alsa_input.pci-0000_00_1b.0.analog-stereo
        Beschreibung: Internes Audio Analog Stereo
        Treiber: module-alsa-card.c
        Sample-Angabe: s16le 2ch 48000Hz
        Kanalzuordnung: front-left,front-right
        Besitzer-Modul: 6
        Stumm: yes
        Lautstärke: 0:  75% 1:  75%
                0: -7,50 dB 1: -7,50 dB
                Verteilung 0,00
        Basis-Lautstärke:  10%
                     -60,75 dB
        Sink-Monitor: k. A.
        Latenz: 3655 usec, eingestellt 20000 usec
        Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        Eigenschaften:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "VT1708S Analog"
                alsa.id = "VT1708S Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xf9ff8000 irq 45"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "3a3e"
                device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Internes Audio Analog Stereo"
                alsa.mixer_name = "VIA VT1708S"
                alsa.components = "HDA:11060397,10438346,00100000"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        Profile:
                analog-input-microphone-front: Mikrofon vorne (priority: 8500, not available)
                analog-input-microphone-rear: Mikrofon hinten (priority: 8200, available)
                analog-input-linein: Line In (priority: 8100, not available)
        Aktive Profile: analog-input-microphone-rear
        Formate:
                pcm

Quelle #3
        Status: RUNNING
        Name: combined.monitor
        Beschreibung: Monitor Source of Simultaneous output to Internes Audio Analog Stereo
        Treiber: module-combine-sink.c
        Sample-Angabe: s16le 2ch 44100Hz
        Kanalzuordnung: front-left,front-right
        Besitzer-Modul: 10
        Stumm: no
        Lautstärke: 0: 100% 1: 100%
                0: 0,00 dB 1: 0,00 dB
                Verteilung 0,00
        Basis-Lautstärke: 100%
                     0,00 dB
        Sink-Monitor: combined
        Latenz: 0 usec, eingestellt 20000 usec
        Flags: DECIBEL_VOLUME LATENCY 
        Eigenschaften:
                device.description = "Monitor Source of Simultaneous output to Internes Audio Analog Stereo"
                device.class = "monitor"
                device.icon_name = "audio-input-microphone"
        Formate:
                pcm

Quelle #4
        Status: RUNNING
        Name: alsa_output.pci-0000_00_1b.0.analog-stereo.equalizer.monitor
        Beschreibung: Monitor of FFT based equalizer on Internes Audio Analog Stereo
        Treiber: module-equalizer-sink.c
        Sample-Angabe: float32le 2ch 44100Hz
        Kanalzuordnung: front-left,front-right
        Besitzer-Modul: 22
        Stumm: no
        Lautstärke: 0: 100% 1: 100%
                0: 0,00 dB 1: 0,00 dB
                Verteilung 0,00
        Basis-Lautstärke: 100%
                     0,00 dB
        Sink-Monitor: alsa_output.pci-0000_00_1b.0.analog-stereo.equalizer
        Latenz: 0 usec, eingestellt 20000 usec
        Flags: DECIBEL_VOLUME LATENCY 
        Eigenschaften:
                device.description = "Monitor of FFT based equalizer on Internes Audio Analog Stereo"
                device.class = "monitor"
                device.icon_name = "audio-input-microphone"
        Formate:
                pcm
```

Can anyone in the forum give me any advise which avenue to follow in order to the get the sound from this usb device, and in combination with the video, eventually?

I suppose the above avconv or an ffmpeg command can be completed with a v4l2 instruction, accordingly.

Sorry for the German terms in the dumps, I am working an a German system. I trust the meanings are intelligible for the English speaking community.
Thanks for your f/b.
frowi

---

### Post by frowi on 2014-03-19
OK, modprobe setting was wrong. For all of you who will encounter the same problem see here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998143)

The workaround is Grabby (while I turned crabby in the process of trying to find a solution):

```
 sudo rmmod em28xx
 sudo modprobe em28xx card=67

```

instead of what would be the correct card

```
 sudo rmmod em28xx
 sudo modprobe em28xx card=68

```

It seems that only mencoder works correctly, here, with avconv or ffmpeg I had to repeat the above settings after each recording session in order to capture sound as well.

I dare not to hope that in one of the next kernel updates this problem may be resolved.

Cheers, frowi

---

