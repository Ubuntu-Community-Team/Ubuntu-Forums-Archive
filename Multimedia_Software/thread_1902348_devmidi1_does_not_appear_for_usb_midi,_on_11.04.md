---
title: "/dev/midi1 does not appear for usb midi, on 11.04"
date: 2011-12-30
forum: Multimedia Software
---

### Post by gregsmith_to on 2011-12-30
When I plug my USB/Midi into my 10.04 machine, a character device /dev/midi1 appears which can be used (e.g. from python) to perform direct MIDI communications. When I plug the same unit into my laptop running 11.04, I don't get that device. 

The device is a M-Audio unit which appears like this on lsusb:

```
Bus 002 Device 007: ID 0763:0150 Midiman M-Audio Uno
```

Other than this, the unit appears to work fine on the 11.04 laptop (works with Rosegarden). It appears in /proc/asound/cards:

```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd5400000 irq 47
 1 [Interface      ]: USB-Audio - USB Uno MIDI Interface
                      M-Audio USB Uno MIDI Interface at usb-0000:00:1d.0-1.3, full speed

```

Is /dev/midi1 a no-longer-supported feature? If so, can it be re-enabled?

I get these in /var/log/syslog when I connect the unit


(on 10.4 machine):

```
Dec 30 13:21:12 ubu kernel: [169744.864300] usb 1-5.4.2: new full speed USB device using ehci_hcd and address 7
Dec 30 13:21:12 ubu kernel: [169744.976114] usb 1-5.4.2: configuration #1 chosen from 1 choice
Dec 30 13:21:13 ubu kernel: [169745.690953] usbcore: registered new interface driver snd-usb-audio
Dec 30 13:21:14 ubu pulseaudio[7795]: module-alsa-card.c: Failed to find a working profile.
Dec 30 13:21:14 ubu pulseaudio[7795]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-M-Audio_USB_Uno_MIDI_Interface-00-Interface" card_name="alsa_card.usb-M-Audio_USB_Uno_MIDI_Interface-00-Interface" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Dec 30 13:21:14 ubu pulseaudio[2658]: module-alsa-card.c: Failed to find a working profile.
Dec 30 13:21:14 ubu pulseaudio[2658]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-M-Audio_USB_Uno_MIDI_Interface-00-Interface" card_name="alsa_card.usb-M-Audio_USB_Uno_MIDI_Interface-00-Interface" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```

The following appears :
```

$ls /dev/midi1 -l
crw-rw----+ 1 root audio 14, 18 2011-12-30 13:21 /dev/midi1

```

On the 11.04 laptop there is this log:

```
Dec 30 13:28:39 theodin kernel: [111901.172772] usb 2-1.3: new full speed USB device using ehci_hcd and address 5
Dec 30 13:28:39 theodin pulseaudio[1392]: module-alsa-card.c: Failed to find a working profile.
Dec 30 13:28:39 theodin pulseaudio[1392]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-M-Audio_USB_Uno_MIDI_Interface-00-Interface" card_name="alsa_card.usb-M-Audio_USB_Uno_MIDI_Interface-00-Interface" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```

And: 
```
lsmod | grep usb
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_wwan               20407  1 option
usbserial              42908  2 option,usb_wwan
usb_storage            53538  0 
snd_usb_audio         112426  0 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96391  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd                    67382  16 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

The version of ubuntu is not the only difference between the two machines, of course, but this seems to be a low-level issue and I'm seeing a different major version after 'usb' in the logs so I suspect that's probably a big factor...

Also, can anyone point me to good overall docs for all of the components in linux audio (alsa, jack, etc), and how they all work together? I tried to set up qsynth on this laptop and all it does is hang hard (killing all audio until next reboot) when I try to load a soundfont. With ubuntu generally I find that basic desktop audio works, but as soon as I try to do anything more sophisticated, it goes downhill pretty quickly, because I don't understand most of what of what I'm trying to configure. The messages about 'module-alsa-card' failures above, for instance, and all the warnings I get from rosegarden when it starts. Wish I knew what was going on -- and I'm prepared to do the reading, but I'd appreciate ideas on the best place to start. 

Thanks, all.

---

