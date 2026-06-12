---
title: "MythBuntu 13.04 Intel HDA and Sound over HDMI"
date: 2013-05-16
forum: Mythbuntu
---

### Post by drumz on 2013-05-16
Prior to upgrading from the previous release, audio over HDMI was working perfectly fine.  Post 13.04 upgrade (and after the kernel upgrade today that  resolved the issue of audio over HDMI device not appearing) I still can't get my frontend to output any audio:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Using speaker-test I get the following:

```
speaker-test -l 2 -c 8 -r 192000 -D hw:0,3

speaker-test 1.0.25

Playback device is hw:0,3
Stream parameters are 192000Hz, S16_LE, 8 channels
Using 16 octaves of pink noise
Playback open error: -19,No such device
```

Anyone have any suggestions?

---

### Post by BicyclerBoy on 2013-05-17
Have a look for the hot-plug events in dmesg..

dmesg | grep -i HDA

Could then check the ELD data in /proc/asound/card0/eld#*

Does the /var/log/Xorg.0.log file show i965 driver working ?

Try speaker-test with -c 2 & -r 48000..

Always rescan audio devices in mythtv FE after kernel/mythtv changes..

---

### Post by drumz on 2013-05-17
```
dmesg | grep -i HDA
[   26.631429] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   26.761465] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   26.761579] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   26.762962] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   26.763064] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   26.763162] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   26.763260] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   26.763356] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   26.763455] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
```

```
more /proc/asound/card0/eld#1.0 
monitor_present         1
eld_valid               1
monitor_name            SHARP HDMI
connection_type         HDMI
eld_version             [0x2] CEA-861D or below
edid_version            [0x3] CEA-861-B, C or D
manufacture_id          0x104d
product_id              0x1011
port_id                 0x0
support_hdcp            0
support_ai              1
audio_sync_delay        0
speakers                [0x1] FL/FR
sad_count               1
sad0_coding_type        [0x1] LPCM
sad0_channels           2
sad0_rates              [0xe0] 32000 44100 48000
sad0_bits               [0x20000] 16

```

```
speaker-test -l 2 -c 8 -r 48000 -D hw:0,3

speaker-test 1.0.25

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 8 channels
Using 16 octaves of pink noise
Playback open error: -19,No such device
```

```
grep 965 /var/log/Xorg.0.log
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
[    29.889] (II) intel(0): [DRI2]   DRI driver: i965
[    30.002] (II) AIGLX: Loaded and initialized i965
```

Here's a copy/paste more generally of the above with the additional lines in between to provide some additional context in case it helps.

```
[    29.889] (II) intel(0): [DRI2] Setup complete
[    29.889] (II) intel(0): [DRI2]   DRI driver: i965
[    29.889] (II) intel(0): direct rendering: DRI2 Enabled
[    29.889] (==) intel(0): hotplug detection: "enabled"
[    29.889] (--) RandR disabled
[    29.897] (II) SELinux: Disabled on system
[    30.002] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    30.002] (II) AIGLX: enabled GLX_INTEL_swap_event
[    30.002] (II) AIGLX: enabled GLX_ARB_create_context
[    30.002] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    30.002] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    30.002] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    30.002] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    30.002] (II) AIGLX: Loaded and initialized i965
[    30.002] (II) GLX: Initialized DRI2 GL provider for screen 0
[    30.003] (II) intel(0): switch to mode 1920x1080 on crtc 3 (pipe 0)
[    30.028] (II) intel(0): Setting screen physical size to 507 x 285
```

---

### Post by BicyclerBoy on 2013-05-17
Your HDMI device does not support 8 channels or rate > 48K..

try
speaker-test -l 2 -c 2 -r 48000 -D hw:0,x
- where x = [0|1|2|3] or just -D hw:0

Correctly functioning video driver is required for HDMI audio.
kernel 3.7 or a patched 3.5 is being recommended for working vaapi on the intel video driver.
These are very likely to contain HDMI HDA audio fixes.

---

### Post by drumz on 2013-05-18
Current kernel is:

```
uname -a
Linux myth1 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:17:37 UTC 2013 i686 i686 i686 GNU/Linux
```

This one runs, but no audio over HDMI:
```
speaker-test -l 2 -c 2 -r 48000 -D hw:0,0

speaker-test 1.0.25

Playback device is hw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.628907
 0 - Front Left                                                                                                                                                                                           
 1 - Front Right             
```

This one runs, but no audio over HDMI:

```
speaker-test -l 2 -c 2 -r 48000 -D hw:0,1
                                                                                                                                                                                                          
speaker-test 1.0.25

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.628935
 0 - Front Left
```

This one gives the error:

```
speaker-test -l 2 -c 2 -r 48000 -D hw:0,2

speaker-test 1.0.25

Playback device is hw:0,2
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -2,No such file or directory
```

And this one gives an error too:

```
speaker-test -l 2 -c 2 -r 48000 -D hw:0,3

speaker-test 1.0.25

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -19,No such device
```

Trying it without the 2nd number doesn't give an error but also no audio over HDMI:

```
speaker-test -l 2 -c 2 -r 48000 -D hw:0

speaker-test 1.0.25

Playback device is hw:0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
```

---

### Post by drumz on 2013-05-18
Meh.  Reading the tail of this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984) it appears that the bug is *still* in kernel 3.8.0.21-32, the fix is in 3.8.0.22 which hasn't been release yet and *not* 3.8.0.21 which just came out.  It appears that I'll have to sit tight until another kernel update is released....

EDIT:  The fix for the HDMI audio issue was apparently regressed so 3.8.0.21 could be quickly released with a security fix but *will* be in 3.8.0.22.  (Referencing post #84 in the above bug link.)

---

