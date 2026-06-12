---
title: "No Sound with Dell latitude D620"
date: 2008-09-10
forum: Multimedia Software
---

### Post by DougAlder on 2008-09-10
I installed Hardy months ago and sound was working fine. One of the updates several days ago seems to have killed my sound. What's weird is that it slowly diminished in volume, I tried changing admin-->Sound-- to autodetect, then STAC then AlSA and briefly got system sounds back but then they disappeared as well. I ran the alsa config and the sound is not muted.  I tried uninstalling ALSA and re-installing it and that hasn't helped. I just tried unloading the reloading ALSA and got the following
> 
root@doug-laptop:/home/doug# alsa force-unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Terminating processes: 6737 7006lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-usb-lib snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

then when i tried to reload them I got

> root@doug-laptop:/home/doug# alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).


Here's the system sound info

> 
Card: HDA Intel                                                              &#9474;
Chip: SigmaTel STAC9200  
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@doug-laptop:/home/doug# modinfo soundcore
filename:       /lib/modules/2.6.24-19-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8alsacfg

depends:        
vermagic:       2.6.24-19-generic SMP mod_unload 586 


root@doug-laptop:/home/doug# lsmod | grep snd
snd_usb_audio          83936  3 
snd_usb_lib            18432  1 snd_usb_audio
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  2 snd_usb_audio,snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  25 snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
usbcore               146028  12 ndiswrapper,usb_storage,pl2303,usbserial,libusual,hci_usb,snd_usb_audio,usbhid,snd_usb_lib,ehci_hcd,uhci_hcd



I also added options snd-hda-intel model=dell-m22 to /etc/modprobe.d/alsa-base

None of this has worked and I'm stymied.I don't understand the error I got when trying to force load ALSA.

This is a dual boot system with XP and the sound works fine in XP so I know it is not a sound card or speaker problem. Any help figuring this out would be greatly appreciated.

---

### Post by DougAlder on 2008-09-10
Just rebooted and checking /var/log/syslog I see the following

> Sep 10 07:20:16 doug-laptop NetworkManager: <debug> [1221056416.265733] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_1'). 
Sep 10 07:20:16 doug-laptop NetworkManager: <debug> [1221056416.271856] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'). 
Sep 10 07:20:16 doug-laptop NetworkManager: <debug> [1221056416.280419] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_1'). 
Sep 10 07:20:16 doug-laptop kernel: [33090.956612] usbcore: deregistering interface driver snd-usb-audio
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.017147] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.024133] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.028368] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.034962] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.040146] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_hw_specific_1'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.046071] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_hw_specific_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.048979] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.050427] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.054773] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0_oss_mixer__1'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.059453] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0_oss_pcm_0_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.063083] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0_oss_pcm_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.067793] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0_alsa_playback_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.071845] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0_alsa_capture_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.075784] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0_alsa_control__1'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.076950] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_47f_ca1_00400_0429034410003_V060000A_if0_sound_card_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.080554] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.084495] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.088913] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Sep 10 07:20:17 doug-laptop NetworkManager: <debug> [1221056417.092703] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer').

Why would it be removing all the sound card functions on boot

---

### Post by DougAlder on 2008-09-10
Running alsamixer I see

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: SigmaTel STAC9200                                                      &#9474;
&#9474;                                                                              &#9474;
&#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[/proc]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474;
&#9474; &#9474;                                                                          # &#9474;
&#9474; &#9474;/proc/asound/version:                                                     # &#9474;
&#9474; &#9474;====================                                                      # &#9474;
&#9474; &#9474;Advanced Linux Sound Architecture Driver Version 1.0.17.                  # &#9474;
&#9474; &#9474;Compiled on Sep 10 2008 for kernel 2.6.24-19-generic (SMP).               # &#9474;
&#9474; &#9474;                                                                          # &#9474;
&#9474; &#9474;/proc/asound/cards:                                                       &#9618; &#9474;
&#9474; &#9474;===================                                                       &#9618; &#9474;
&#9474; &#9474; 0 [Intel          ]: HDA-Intel - HDA Intel                               &#9618; &#9474;
&#9474; &#9474;                      HDA Intel at 0xdfffc000 irq 20                      &#9618; &#9474;
&#9474; &#9474; 1 [Headset        ]: USB-Audio - Plantronics Headset                     &#9618; &#9474;
&#9474; &#9474;                      Plantronics Plantronics Headset at usb-0000:00:1d.2-&#9618; &#9474;
&#9474; &#9474;                                                                          &#9618; &#9474;
&#9474; &#9474;/proc/asound/devices:                                                     &#9618; &#9474;
&#9474; &#9474;=====================                                                     &#9618; &#9474;
&#9474; &#9474;  0: [ 0]   : control                                                     &#9618; &#9474;
&#9474; &#9474;  1:        : sequencer                                                   &#9618; &#9474;
&#9474; &#9492;###############################################################&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9496;

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: SigmaTel STAC9200                                                      &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-3.00, -3.00]                                          &#9474;
&#9474;                                                                              &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                                      &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;  &#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                      &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9500;&#9472;&#9472;&#9508;          &#9492;&#9472;&#9472;&#9496;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;         &#9474;OO&#9474;                        &#9474;OO&#9474;          &#9474;OO&#9474;                       &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;                       &#9474;
&#9474;        94<>94        92<>92                                    75<>75        &#9474;
&#9474;      < Master >       PCM          IEC958       IEC958 D      Capture        &#9474;
 &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;



```

---

### Post by DougAlder on 2008-09-11
Fixed - turned out to be a faulty cable

---

