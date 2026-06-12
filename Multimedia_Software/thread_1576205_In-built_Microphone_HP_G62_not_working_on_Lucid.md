---
title: "In-built Microphone HP G62 not working on Lucid"
date: 2010-09-16
forum: Multimedia Software
---

### Post by vaietc on 2010-09-16
Hi

Ok, the title text says it all. When I used gnome-sound-recorder I can only hear noise instead of any voice recording. The mic was working just fine till day before yesterday. Not sure what happened all of a sudden. I even followed the steps here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

which had helped me once before but not this time. I'm not sure what else to do - any help would be greatly appreciated. 

 - Vaibhav

---

### Post by lidex on 2010-09-17
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by vaietc on 2010-09-17
Hi

Thanks for the reply. I already did that, bug report [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/640982"). No movement on it though, so thought I'd post here in case someone else had the same issue

- Vaibhav

---

### Post by lidex on 2010-09-17
Looks like this happened recently:
> AlsaVersion:
 Advanced Linux Sound Architecture Driver Version 1.0.23.
 Compiled on Sep 16 2010 for kernel 2.6.32-24-generic (SMP).
Can you post this info please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by vaietc on 2010-09-20
Hi

Sorry about the late response, outputs as follows:


$ uname -a
```

Linux vaibhav-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

```
$aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```$ dpkg -l | grep "alsa"
```

ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-24-generic    2.6.32-24.201009160500                          Ubuntu-supplied Linux modules for version 2.

```And a huge output now:
$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

[   21.418026]   alloc kstat_irqs on node -1
[   21.418035] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.418095]   alloc irq_desc for 34 on node -1
[   21.418097]   alloc kstat_irqs on node -1
[   21.418112] HDA Intel 0000:00:1b.0: irq 34 for MSI/MSI-X
[   21.418149] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.418156] ALSA hda_intel.c:2545: chipset global capabilities = 0x4401
[   21.420574] vga16fb: initializing
--
[   21.420583] vga16fb: not registering due to another framebuffer present
[   21.449853] ALSA hda_intel.c:909: codec_mask = 0x9
[   21.449962] ALSA hda_intel.c:1347: codec #0 probed OK
[   21.450006] ALSA hda_intel.c:1347: codec #3 probed OK
[   21.473560] ALSA patch_realtek.c:1482: SKU: Nid=0x1d sku_cfg=0x4017992d
[   21.473564] ALSA patch_realtek.c:1484: SKU: port_connectivity=0x1
[   21.473567] ALSA patch_realtek.c:1485: SKU: enable_pcbeep=0x1
[   21.473570] ALSA patch_realtek.c:1486: SKU: check_sum=0x00000007
[   21.473572] ALSA patch_realtek.c:1487: SKU: customization=0x00000099
[   21.473575] ALSA patch_realtek.c:1488: SKU: external_amp=0x5
[   21.473577] ALSA patch_realtek.c:1489: SKU: platform_type=0x1
[   21.473579] ALSA patch_realtek.c:1490: SKU: swap=0x0
[   21.473581] ALSA patch_realtek.c:1491: SKU: override=0x1
[   21.474015] hda_codec: ALC259: BIOS auto-probing.
[   21.474020] ALSA hda_codec.c:4613: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   21.474023] ALSA hda_codec.c:4617:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.474025] ALSA hda_codec.c:4621:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   21.474027] ALSA hda_codec.c:4622:    mono: mono_out=0x0
[   21.474029] ALSA hda_codec.c:4626:    inputs:
[   21.474031] ALSA hda_codec.c:4630:  Mic=0x18
[   21.474034] ALSA hda_codec.c:4630:  Internal Mic=0x19
[   21.474036] ALSA hda_codec.c:4632: 
[   21.474457] ALSA patch_realtek.c:1532: realtek: No valid SSID, checking pincfg 0x4017992d for NID 0x1d
[   21.474460] ALSA patch_realtek.c:1548: realtek: Enabling init ASM_ID=0x992d CODEC_ID=10ec0270
[   21.474462] ALSA patch_realtek.c:1381: realtek: Enable HP auto-muting on NID 0x21
[   21.474467] ALSA patch_realtek.c:1426: realtek: Enable auto-mic switch on NID 0x18/0x19
[   21.475377] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   21.482862] ALSA hda_codec.c:2145: Cannot find slave Front Playback Volume, skipped
[   21.482865] ALSA hda_codec.c:2145: Cannot find slave Surround Playback Volume, skipped
[   21.482868] ALSA hda_codec.c:2145: Cannot find slave Center Playback Volume, skipped
[   21.482870] ALSA hda_codec.c:2145: Cannot find slave LFE Playback Volume, skipped
[   21.482872] ALSA hda_codec.c:2145: Cannot find slave Side Playback Volume, skipped
[   21.482877] ALSA hda_codec.c:2145: Cannot find slave Mono Playback Volume, skipped
[   21.482879] ALSA hda_codec.c:2145: Cannot find slave Line-Out Playback Volume, skipped
[   21.482881] ALSA hda_codec.c:2145: Cannot find slave PCM Playback Volume, skipped
[   21.482886] ALSA hda_codec.c:2145: Cannot find slave Front Playback Switch, skipped
[   21.482889] ALSA hda_codec.c:2145: Cannot find slave Surround Playback Switch, skipped
[   21.482891] ALSA hda_codec.c:2145: Cannot find slave Center Playback Switch, skipped
[   21.482893] ALSA hda_codec.c:2145: Cannot find slave LFE Playback Switch, skipped
[   21.482895] ALSA hda_codec.c:2145: Cannot find slave Side Playback Switch, skipped
[   21.482899] ALSA hda_codec.c:2145: Cannot find slave Mono Playback Switch, skipped
[   21.482902] ALSA hda_codec.c:2145: Cannot find slave IEC958 Playback Switch, skipped
[   21.482904] ALSA hda_codec.c:2145: Cannot find slave Line-Out Playback Switch, skipped
[   21.482906] ALSA hda_codec.c:2145: Cannot find slave PCM Playback Switch, skipped
[   21.483269] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   21.483350] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.569181] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xe40000
--
[   24.369094]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[   24.436057] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.436063] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.436266] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.436270] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.436523] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.436527] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.436860] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.436863] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.437015] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.437018] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.437175] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.437178] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.437382] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.437384] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.437781] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.437786] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.438001] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.438005] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.438217] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.438221] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.438517] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.438521] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.439002] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.439007] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.439225] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.439230] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.439440] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.439444] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.439737] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.439741] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.440128] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.440131] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.440292] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.440295] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.440441] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.440444] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.440744] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.440749] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.441103] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.441106] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.443949] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.443962] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   24.448511] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   24.456535] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.456548] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   24.456554] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   24.456902] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.457122] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.457434] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.457926] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.458583] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.458595] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.464484] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.464495] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.464518] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.464536] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.465459] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.465464] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.465477] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.465481] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.466100] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   24.466114] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   24.472452] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   24.480468] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   24.480486] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   24.480492] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   24.480802] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.481010] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.481310] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.481795] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.482469] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.482481] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.482501] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.482511] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.482530] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.482547] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.483419] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.483424] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.483437] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.483441] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.483878] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.483882] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.484297] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.484302] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.484810] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.484814] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.485251] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.485255] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.485667] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.485672] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.486081] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.486085] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.486518] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.486523] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.486959] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.486964] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.487379] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.487383] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.487794] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.487799] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.488230] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.488235] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.488684] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.488688] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.489101] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.489106] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.489516] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.489520] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.489956] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.489961] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.490400] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.490404] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.490820] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.490824] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.491243] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.491248] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.491681] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.491685] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.492128] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.492132] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.492570] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.492575] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.492980] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.492984] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.493411] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.493416] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.493850] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.493854] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.494267] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.494271] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.494704] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.494708] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.495139] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.495143] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.495581] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.495585] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.496006] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.496010] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.496446] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.496452] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.496890] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.496894] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.497336] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.497341] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.497791] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.497796] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.498213] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.498217] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.498650] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.498654] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.499099] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.499103] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.499514] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.499518] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.499934] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.499938] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.500436] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.500440] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.500884] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.500888] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.501368] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.501373] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.501844] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.501849] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.502481] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.502486] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.503362] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.503366] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.503859] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.503863] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.504337] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.504342] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.504978] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.504983] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.505801] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.505805] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.506281] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.506285] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.506761] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.506765] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.507403] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.507408] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.508225] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.508230] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.508760] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.508764] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.509191] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.509195] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.509810] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.509814] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.510658] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.510663] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.511156] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.511160] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.511621] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.511626] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.512248] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.512253] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.513160] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.513165] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.513648] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.513652] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.514109] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.514114] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.514755] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.514760] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.515560] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.515563] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.516030] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.516035] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.516510] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.516515] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.517139] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.517143] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.517951] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.517955] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.518408] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.518412] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.518875] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.518879] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.519398] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.519401] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.519947] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.519950] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.520273] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.520276] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.520629] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.520632] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.521043] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.521046] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.521585] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.521588] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.521901] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.521904] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.522213] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.522216] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.522625] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.522628] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.523168] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.523171] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   24.526528] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.526642] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x4, pinctl=0x40
[   24.526686] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   24.526731] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x6, pinctl=0x40
[   24.526734] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x8, channel=0, format=0x4011
[   24.532413] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.532548] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x4, pinctl=0x40
[   24.532595] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   24.532651] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x6, pinctl=0x40
[   24.532655] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x8, channel=0, format=0x4011
[   24.532984] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.533198] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.533506] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.533969] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.534634] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.534647] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.534667] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.534677] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.534698] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.534714] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.535602] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.535642] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   24.535866] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.536079] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.536397] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.536883] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.537439] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.537449] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.537466] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   24.537474] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.537488] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.537502] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   24.539307] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   24.539319] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   24.548077] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   24.552599] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   24.552610] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   24.552613] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   24.559799] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   24.559810] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   24.559827] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   24.559835] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   29.566693] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   29.566720] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   30.724230] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   30.724233] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   30.724247] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   30.724249] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   31.473769] ip_tables: (C) 2000-2006 Netfilter Core Team
--
[   31.486589] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   32.323976] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.323982] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.324207] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.324212] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.324548] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.324552] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.325030] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.325034] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.325262] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.325265] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.325490] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.325494] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.325788] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.325792] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.326281] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.326285] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.326510] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.326514] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.326725] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.326729] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.327031] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.327035] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.327488] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.327491] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.327659] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.327662] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.327813] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.327815] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.328022] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.328025] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.328350] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.328353] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.328509] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.328512] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.328660] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.328663] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.328868] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.328871] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.329193] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.329196] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.332020] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.332033] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   32.332037] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   32.332054] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.332063] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   32.332067] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   32.332247] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.332399] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.332612] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.332939] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.333380] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.333390] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.333406] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.333415] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.333429] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.333446] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.334072] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.334075] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.334086] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.334089] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.334632] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   32.334646] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   32.346198] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   32.354196] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   32.354210] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   32.354215] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   32.354571] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.354801] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.355114] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.355599] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.356270] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.356283] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.356303] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.356313] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.356332] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.356352] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.357297] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.357301] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.357319] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.357322] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.357797] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.357801] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.358496] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.358500] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.358958] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.358963] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.359404] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.359408] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.359825] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.359830] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.360258] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.360263] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.360685] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.360689] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.361125] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.361129] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.361555] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.361559] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.361970] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.361974] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.362653] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.362658] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.363108] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.363112] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.363529] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.363534] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.363957] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.363962] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.364426] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.364430] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.364900] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.364904] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.365354] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.365358] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.365753] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.365758] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.366393] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.366397] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.366859] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.366863] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.367291] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.367295] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.367714] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.367718] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.368167] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.368170] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.368634] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.368638] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.369076] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.369081] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.369510] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.369514] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.369946] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.369949] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.370609] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.370614] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.371044] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.371048] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.371467] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.371471] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.371914] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.371918] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.372376] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.372381] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.372817] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.372821] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.373241] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.373245] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.373692] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.373696] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.374450] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.374454] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.374900] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.374904] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.375326] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.375330] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.375772] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.375775] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.376234] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.376238] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.376737] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.376741] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.377244] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.377249] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.377857] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.377861] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.378891] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.378896] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.379408] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.379412] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.379899] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.379903] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.380530] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.380534] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.381364] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.381369] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.381871] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.381875] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.382537] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.382541] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.383188] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.383193] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.384037] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.384042] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.384533] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.384538] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.385024] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.385029] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.385672] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.385677] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.386669] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.386674] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.387166] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.387170] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.387632] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.387636] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.388257] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.388262] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.389078] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.389082] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.389574] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.389578] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.390060] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.390065] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.390902] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.390907] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.391736] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.391740] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.392218] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.392222] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.392697] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.392702] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.393317] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.393321] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.394302] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.394306] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.394807] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.394811] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.395294] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.395298] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.395928] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.395932] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.396763] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.396767] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.397264] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.397269] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.397751] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.397755] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.398572] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.398577] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.399409] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.399414] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.399906] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.399910] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.400388] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.400392] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.401042] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.401047] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.401849] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.401854] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   32.407370] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.407463] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x4, pinctl=0x40
[   32.407510] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   32.407567] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x6, pinctl=0x40
[   32.407571] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x8, channel=0, format=0x4011
[   32.407592] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.407697] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x4, pinctl=0x40
[   32.407753] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   32.407831] ALSA patch_hdmi.c:733: hdmi_setup_stream: NID=0x6, pinctl=0x40
[   32.407835] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x8, channel=0, format=0x4011
[   32.408088] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.408314] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.408622] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.409114] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.409773] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.409785] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.409805] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.409814] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.409835] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.409856] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.411046] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.411093] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   32.411332] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.411543] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.411844] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.412317] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.412951] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.412963] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.412983] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   32.412993] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.413013] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.413034] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   32.415800] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4013
[   32.415816] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   32.415822] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   32.415842] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4013
[   32.415853] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   32.415858] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   32.444092] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   32.444107] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.444127] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   32.444137] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.896554] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
--
[   36.071637] dm_check_edca_turbo():iot peer is unknown, bssid:00:1f:fe:1c:03:b9
[   37.484885] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   37.484913] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x8
[   37.485788] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   37.485793] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   37.485813] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x2
[   37.485817] ALSA hda_codec.c:1284: hda_codec_cleanup_stream: NID=0x3
[   45.087507] wlan0: no IPv6 routers present
--
[  712.640450] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 4,is_mesh is 0
[  718.787179] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4013
[  718.787194] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[  718.787198] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[  718.787215] ALSA hda_intel.c:1671: azx_pcm_prepare: bufsize=0x10000, format=0x4013
[  718.787224] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[  718.787227] ALSA hda_codec.c:1226: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[  724.905852] DHCP pkt src port:68, dest port:67!!
--
[  782.804117] DHCP pkt src port:68, dest port:67!!
[  800.730415] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  801.767660] DHCP pkt src port:68, dest port:67!!

```Hope that helps you help me! 

- Vaibhav

---

### Post by lidex on 2010-09-21
Try updating alsa to v. 1.0.23 using the link in my sig.

---

### Post by vaietc on 2010-09-22
Thank you Lidex! Worked like a charm!

---

### Post by vaietc on 2010-09-25
I have a really interesting issue now. I applied the new drivers as mentioned by Lidex and my mic started working just fine. As does my audio in general. However, my VLC player is acting a bit weird. I get sound when I log in but if I close vlc and play a different file, I get no sound from it. A log out fixes that temporarily but I wouldn't want that to be a permanent solution. Secondly, whenever I have sound in VLC, it isn't affected by the standard volume controls, it seems to depend only on the sounds within the player. This gets me thinking that my player is not mapped to the correct drivers - any suggestions/comments on this one?

---

### Post by lidex on 2010-09-26
> **vaietc said:**
> I have a really interesting issue now. I applied the new drivers as mentioned by Lidex and my mic started working just fine. As does my audio in general. However, my VLC player is acting a bit weird. I get sound when I log in but if I close vlc and play a different file, I get no sound from it. A log out fixes that temporarily but I wouldn't want that to be a permanent solution. Secondly, whenever I have sound in VLC, it isn't affected by the standard volume controls, it seems to depend only on the sounds within the player. This gets me thinking that my player is not mapped to the correct drivers - any suggestions/comments on this one?
Check in VLC 'Tools>Preferences>Audio' the 'Output Module'

---

