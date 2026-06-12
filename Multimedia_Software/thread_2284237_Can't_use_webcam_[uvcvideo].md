---
title: "Can't use webcam [uvcvideo]"
date: 2015-06-28
forum: Multimedia Software
---

### Post by andrew243 on 2015-06-28
The webcam is successfully detected, the modules are loaded, but cheese can't open the stream (or VLC).
Output of lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 020: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Output of lsmod
```
Module                  Size  Used by
ctr                    16384  3 
ccm                    20480  3 
arc4                   16384  2 
b43legacy             106496  0 
b43                   401408  0 
bcma                   49152  1 b43
mac80211              626688  2 b43,b43legacy
ssb                    57344  2 b43,b43legacy
cfg80211              462848  3 b43,mac80211,b43legacy
binfmt_misc            20480  1 
[B]uvcvideo               73728  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              139264  3 uvcvideo,v4l2_common,videobuf2_core[/B]
** media                  24576  2 uvcvideo,videodev**
acer_wmi               20480  0 
snd_hda_codec_realtek    73728  1 
sparse_keymap          16384  1 acer_wmi
snd_hda_codec_generic    65536  1 snd_hda_codec_realtek
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
coretemp               16384  0 
joydev                 20480  0 
lpc_ich                20480  0 
serio_raw              16384  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
snd                    69632  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
shpchp                 32768  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                40960  3 lp,ppdev,parport_pc
autofs4                40960  2 
xts                    16384  1 
gf128mul               16384  1 xts
dm_crypt               24576  1 
i915                  937984  2 
psmouse               106496  0 
pata_acpi              16384  0 
i2c_algo_bit           16384  1 i915
atl1c                  40960  0 
drm_kms_helper        110592  1 i915
drm                   286720  4 i915,drm_kms_helper
wmi                    20480  1 acer_wmi
video                  20480  2 i915,acer_wmi

```
I did `echo 0xffff > /sys/module/uvcvideo/parameters/trace
dmesg shows me this every time i try to open the webcam stream
```

[73578.775286] uvcvideo: uvc_v4l2_open
[73578.858256] uvcvideo: Resuming interface 0
[73578.858266] uvcvideo: Resuming interface 1
[73578.861359] uvcvideo: uvc_v4l2_release
[73578.869062] uvcvideo: uvc_v4l2_open
[73578.871506] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73578.871518] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.891306] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73578.891321] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.903496] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[73578.903510] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.915316] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[73578.915330] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.928442] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[73578.928455] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.943260] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[73578.943272] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.954396] uvcvideo: Trying format 0x56595559 (YUYV): 352x288.
[73578.954406] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.966283] uvcvideo: Trying format 0x56595559 (YUYV): 352x288.
[73578.966293] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.977377] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[73578.977387] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73578.991915] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[73578.991929] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.009576] uvcvideo: uvc_v4l2_release
[73579.332529] uvcvideo: uvc_v4l2_open
[73579.336812] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73579.336827] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.349749] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73579.349763] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.366634] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[73579.366648] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.377363] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[73579.377375] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.389430] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[73579.389443] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.401561] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[73579.401575] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.416826] uvcvideo: Trying format 0x56595559 (YUYV): 352x288.
[73579.416838] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.428408] uvcvideo: Trying format 0x56595559 (YUYV): 352x288.
[73579.428421] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.440421] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[73579.440434] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.451311] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[73579.451323] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.785559] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73579.785572] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.804654] uvcvideo: Setting frame interval to 1/30 (333333).
[73579.834776] uvcvideo: uvc_v4l2_release
[73579.847129] uvcvideo: uvc_v4l2_open
[73579.851583] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73579.851597] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.867582] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73579.867596] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.881437] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[73579.881450] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.892355] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[73579.892368] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.903522] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[73579.903535] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.913348] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[73579.913361] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.927119] uvcvideo: Trying format 0x56595559 (YUYV): 352x288.
[73579.927133] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.944368] uvcvideo: Trying format 0x56595559 (YUYV): 352x288.
[73579.944382] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.958437] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[73579.958447] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73579.969349] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[73579.969359] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73580.130490] uvcvideo: Trying format 0x56595559 (YUYV): 640x480.
[73580.130505] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[73580.150372] uvcvideo: Setting frame interval to 1/30 (333333).
[73581.560864] uvcvideo: Control 0x00980927 not found.
[73581.562797] uvcvideo: uvc_v4l2_mmap
[73581.562966] uvcvideo: uvc_v4l2_mmap
[73581.572119] uvcvideo: Device requested 3072 B/frame bandwidth.
**[73581.572131] uvcvideo: No fast enough alt setting for requested bandwidth.**
[73581.574452] uvcvideo: uvc_v4l2_poll
[73581.632453] uvcvideo: uvc_v4l2_release
[73583.988182] uvcvideo: Suspending interface 1
[73583.988199] uvcvideo: Suspending interface 0

```
If i set the Bandwidth fix quirk, the requested bandwidth goes up to 19058 B/frame

---

