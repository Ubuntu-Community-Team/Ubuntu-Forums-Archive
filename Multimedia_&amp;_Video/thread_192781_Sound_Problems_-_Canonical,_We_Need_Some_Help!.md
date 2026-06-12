---
title: "Sound Problems - Canonical, We Need Some Help!"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by 3saul on 2006-06-09
I have an Echoaudio darla20 card which worked fine in Breezy...but not in dapper.

Here is the output of lsmod | grep snd
snd_seq_dummy 3972 0
snd_seq_oss 39136 0
snd_seq_midi 9248 0
snd_rawmidi 27072 1 snd_seq_midi
snd_seq_midi_event 7520 2 snd_seq_oss,snd_seq_midi
snd_seq 58704 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device 9452 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_darla20 24580 0
snd_pcm_oss 45888 0
snd_mixer_oss 20160 1 snd_pcm_oss
snd_pcm 96420 2 snd_darla20,snd_pcm_oss
snd_timer 27044 2 snd_seq,snd_pcm
snd 60388 10 snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_darla20,snd_pcm_oss,snd_mixer_oss,s nd_pcm,snd_timer
soundcore 10784 1 snd
snd_page_alloc 11336 2 snd_darla20,snd_pcm

As you can see it has in fact loaded the driver. But when I do a cat /proc/asound/cards I get:
No soundcard. Also, trying to run echomixer says that it can't find an echo card. HAL can see it:

udi = '/org/freedesktop/Hal/devices/pci_1057_1801'
info.udi = '/org/freedesktop/Hal/devices/pci_1057_1801' (string)
linux.subsystem = 'pci' (string)
linux.hotplug_type = 1 (0x1) (int)
pci.subsys_product = 'Darla' (string)
pci.subsys_vendor = 'Echo Digital Audio Corporation' (string)
info.product = 'DSP56301 Digital Signal Processor' (string)
pci.product = 'DSP56301 Digital Signal Processor' (string)
info.vendor = 'Motorola' (string)
pci.vendor = 'Motorola' (string)
pci.device_protocol = 0 (0x0) (int)
pci.device_subclass = 128 (0x80) (int)
pci.device_class = 4 (0x4) (int)
pci.subsys_vendor_id = 60608 (0xecc0) (int)
pci.subsys_product_id = 16 (0x10) (int)
pci.vendor_id = 4183 (0x1057) (int)
pci.product_id = 6145 (0x1801) (int)
pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:06.0' (string)
info.parent = '/org/freedesktop/Hal/devices/pci_10de_ed' (string)
info.bus = 'pci' (string)
linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:06.0' (string)
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:06.0' (string)

Any other idea's?

---

