---
title: "snd_usb_audio: disagrees about version of symbol xxx"
date: 2009-07-18
forum: Multimedia Software
---

### Post by bartek on 2009-07-18
I upgraded to alsa 1.0.20, after which my pluggable USB headset stopped working. I do have "regular" sound.

Unsure how to handle what I get after probing for my headset:

```
$ sudo modprobe snd-usb-audio
WARNING: Error inserting snd_usb_lib (/lib/modules/2.6.24-24-generic/ubuntu/sound/alsa-driver/modules/snd-usb-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.24-24-generic/ubuntu/sound/alsa-driver/modules/snd-usb-audio.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg says:

```
[  196.460256] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[  196.471333] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  196.479324] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
[  196.487309] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0
[  196.496202] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[  196.503286] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  196.511271] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
[  196.519259] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0

```

Also below that it continues with?

```
[  214.016196] snd_usb_lib: disagrees about version of symbol snd_rawmidi_receive
[  214.016203] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[  214.016298] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_empty
[  214.016303] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[  214.016349] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit
[  214.016352] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[  214.016522] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_ack
[  214.016525] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[  214.016641] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_peek
[  214.016643] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[  214.016750] snd_usb_lib: disagrees about version of symbol snd_rawmidi_new
[  214.016752] snd_usb_lib: Unknown symbol snd_rawmidi_new
[  214.016800] snd_usb_lib: disagrees about version of symbol snd_rawmidi_set_ops
[  214.016804] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[  214.018498] snd_usb_audio: disagrees about version of symbol snd_ctl_add
[  214.018503] snd_usb_audio: Unknown symbol snd_ctl_add
[  214.018555] snd_usb_audio: disagrees about version of symbol snd_pcm_new
[  214.018559] snd_usb_audio: Unknown symbol snd_pcm_new
[  214.018679] snd_usb_audio: disagrees about version of symbol snd_card_register
[  214.018683] snd_usb_audio: Unknown symbol snd_card_register
[  214.018734] snd_usb_audio: disagrees about version of symbol snd_card_free
[  214.018737] snd_usb_audio: Unknown symbol snd_card_free
[  214.018794] snd_usb_audio: disagrees about version of symbol snd_card_proc_new
[  214.018798] snd_usb_audio: Unknown symbol snd_card_proc_new
[  214.018858] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[  214.018956] snd_usb_audio: disagrees about version of symbol snd_pcm_stop
[  214.018960] snd_usb_audio: Unknown symbol snd_pcm_stop
[  214.019006] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[  214.019009] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[  214.019130] snd_usb_audio: disagrees about version of symbol snd_ctl_find_id
[  214.019134] snd_usb_audio: Unknown symbol snd_ctl_find_id
[  214.019237] snd_usb_audio: disagrees about version of symbol snd_ctl_new1
[  214.019239] snd_usb_audio: Unknown symbol snd_ctl_new1
[  214.019296] snd_usb_audio: disagrees about version of symbol snd_component_add
[  214.019300] snd_usb_audio: Unknown symbol snd_component_add
[  214.019347] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_rule_add
[  214.019351] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[  214.019505] snd_usb_audio: disagrees about version of symbol snd_ctl_boolean_mono_info
[  214.019509] snd_usb_audio: Unknown symbol snd_ctl_boolean_mono_info
[  214.019556] snd_usb_audio: disagrees about version of symbol snd_pcm_lib_ioctl
[  214.019560] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[  214.019612] snd_usb_audio: disagrees about version of symbol snd_hwdep_new
[  214.019616] snd_usb_audio: Unknown symbol snd_hwdep_new
[  214.019668] snd_usb_audio: disagrees about version of symbol snd_pcm_new_stream
[  214.019672] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[  214.019848] snd_usb_audio: disagrees about version of symbol snd_card_free_when_closed
[  214.019851] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[  214.019908] snd_usb_audio: disagrees about version of symbol snd_ctl_notify
[  214.019910] snd_usb_audio: Unknown symbol snd_ctl_notify
[  214.020005] snd_usb_audio: disagrees about version of symbol snd_pcm_set_ops
[  214.020008] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[  214.020106] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_list
[  214.020109] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[  214.020209] snd_usb_audio: disagrees about version of symbol snd_device_new
[  214.020213] snd_usb_audio: Unknown symbol snd_device_new
[  214.020368] snd_usb_audio: disagrees about version of symbol snd_pcm_suspend_all
[  214.020372] snd_usb_audio: Unknown symbol snd_pcm_suspend_all
[  214.020440] snd_usb_audio: disagrees about version of symbol snd_card_disconnect
[  214.020444] snd_usb_audio: Unknown symbol snd_card_disconnect
[  214.020698] snd_usb_audio: Unknown symbol snd_card_create
[  214.020747] snd_usb_audio: disagrees about version of symbol snd_pcm_period_elapsed
[  214.020750] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[  214.020837] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect

```

ideas?

---

### Post by bartek on 2009-07-20
I eliminated the headset itself as the cause of the problem, works perfectly on my laptop, also running the same flavor of Ubuntu

---

### Post by sub.mesa on 2009-08-22
Too bad you never get an answer here. But i appear to have the same problem with Ubuntu 9.04 and a Creative XMOD USB audio device, which worked for several years with Ubuntu until today.

My dmesg shows:
[   16.404644] snd_usb_lib: disagrees about version of symbol snd_rawmidi_receive
[   16.404646] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[   16.404754] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_empty
[   16.404755] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[   16.404810] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit
[   16.404811] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[   16.404913] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_ack
[   16.404914] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[   16.405013] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_peek
[   16.405014] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[   16.405102] snd_usb_lib: disagrees about version of symbol snd_rawmidi_new
[   16.405103] snd_usb_lib: Unknown symbol snd_rawmidi_new
[   16.405148] snd_usb_lib: disagrees about version of symbol snd_rawmidi_set_ops
[   16.405149] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops

Honestly, it has been such a pain to get simple stereo sound working on Ubuntu, and to keep it working. I really hope 9.10 improves on this, all the Pulseaudio utilities never worked for me and gave me zero control (selecting default sound card; doesn't work you have to disable all other sound devices in BIOS).

I did leave my PC on for some weeks, so the issue i have might be related to yours. Perhaps trying to manually update ALSA might help?

---

### Post by sub.mesa on 2009-08-22
I managed to resolve this problem by installing ALSA 1.0.20 using these instructions:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

Apparantly, having PulseAudio as default audio source doesn't mean PulseAudio communicates with the soundcard directly. So in order to get sound, you need to have Pulseaudio, ALSA and OSS working. However, i would argue that the more software required for simple operations (stereo audio) would complicate things and introduce strange bugs.

Also, even with the audio working right now, it may break in the future. Synaptic still shows ALSA 1.0.18 installed, while "cat /proc/asound/version" shows version 1.0.20. Installing software this way leads to a junk configuration and many things can go wrong.

Boy i miss the days i worked with FreeBSD which simply had the latest releases of all major software in the portstree. I seriously dislike the keeping-you-in-the-stoneage philosophy of Debian-derived distributions. People don't settle for that, and will tune/install/configure things to get it working, but that's not the proper way to do it.

---

