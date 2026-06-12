---
title: "sound problem"
date: 2008-10-12
forum: Multimedia Software
---

### Post by desimoviebuff on 2008-10-12
hi this is the first time i am posting though i have been a grateful user of this forum to learn and sort out issues in Kubuntu. 

issue: recently upgraded my mobo, cpu but still using the old installation of hardy heron. currently no sound. went thru the guide on this forum but unable to figure out the issue. here is my lspci out put(ONLY PART OF THE OUTPUT)
lspci -v
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8336
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8336
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at cc00 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Eaglelake HECI Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8336
        Flags: bus master, fast devsel, latency 0
        Memory at fe800000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4 (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 82d4
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at c480 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5 (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 82d4
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6 (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 82d4
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at c880 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2 (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 82d4
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fe3fbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Unknown device 82fe
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fe3f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
Here are the other outputs that may help
vs@vs-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
vs@vs-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
vs@vs-desktop:~$ sudo lsmod|grep snd
[sudo] password for vs:
snd_hda_intel         344728  1
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

---

