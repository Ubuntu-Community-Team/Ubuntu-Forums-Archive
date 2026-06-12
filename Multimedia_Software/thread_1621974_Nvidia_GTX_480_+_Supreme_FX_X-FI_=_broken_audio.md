---
title: "Nvidia GTX 480 + Supreme FX X-FI = broken audio"
date: 2010-11-14
forum: Multimedia Software
---

### Post by CMDR:ZOD on 2010-11-14
Hey,

So I went and bought 3 480 gtx's and sli'd them in linux. Works well enough (well not really), but the big issue is what happens when I enable the Supreme FX X-FI soundcard with these video cards install. HDMI audio on these gtx 480's work well on my single display, but when the supreme fx is enabled audio is broken for these two sound devices (the gtx 480 audio and supreme fx). The nvidia audio devices still show up in pulse but the supreme fx will not. Audio still works when I connect my bluetooth headset so I know the sound server is still working. I am pretty sure it is a clash because both devices use the HDA_Intel driver. Heres a clip from my kern.log

ov 14 19:23:13 zod kernel: [   17.729623] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
Nov 14 19:23:13 zod kernel: [   17.784282] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 14 19:23:13 zod kernel: [   17.787023] EXT4-fs (sdc1): re-mounted. Opts: commit=0
Nov 14 19:23:14 zod kernel: [   18.732127] hda-intel: No response from codec, disabling MSI: last cmd=0x100f0000
Nov 14 19:23:14 zod kernel: [   19.374455] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input4
Nov 14 19:23:15 zod kernel: [   19.734168] hda-intel: Codec #1 probe error; disabling it...
Nov 14 19:23:15 zod kernel: [   19.765686] hda-intel: no codecs initialized
Nov 14 19:23:15 zod kernel: [   19.765843] HDA Intel 0000:00:1b.0: PCI INT A disabled
Nov 14 19:23:15 zod kernel: [   19.765873]   alloc irq_desc for 34 on node -1
Nov 14 19:23:15 zod kernel: [   19.765875]   alloc kstat_irqs on node -1
Nov 14 19:23:15 zod kernel: [   19.765883] HDA Intel 0000:02:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
Nov 14 19:23:15 zod kernel: [   19.765888] hda_intel: Disable MSI for Nvidia chipset
Nov 14 19:23:15 zod kernel: [   19.765889] hda_intel: codec_mask forced to 0x2
Nov 14 19:23:15 zod kernel: [   19.765909] HDA Intel 0000:02:00.1: setting latency timer to 64
Nov 14 19:23:15 zod kernel: [   19.981534]   alloc irq_desc for 37 on node -1
Nov 14 19:23:15 zod kernel: [   19.981536]   alloc kstat_irqs on node -1
Nov 14 19:23:15 zod kernel: [   19.981541] HDA Intel 0000:03:00.1: PCI INT B -> GSI 37 (level, low) -> IRQ 37
Nov 14 19:23:15 zod kernel: [   19.981543] hda_intel: Disable MSI for Nvidia chipset
Nov 14 19:23:15 zod kernel: [   19.981567] HDA Intel 0000:03:00.1: setting latency timer to 64
Nov 14 19:23:16 zod kernel: [   20.772465]   alloc irq_desc for 42 on node -1
Nov 14 19:23:16 zod kernel: [   20.772467]   alloc kstat_irqs on node -1
Nov 14 19:23:16 zod kernel: [   20.772473] HDA Intel 0000:04:00.1: PCI INT B -> GSI 42 (level, low) -> IRQ 42
Nov 14 19:23:16 zod kernel: [   20.772475] hda_intel: Disable MSI for Nvidia chipset
Nov 14 19:23:16 zod kernel: [   20.772504] HDA Intel 0000:04:00.1: setting latency timer to 64
Nov 14 19:23:16 zod kernel: [   21.636769] ppdev: user-space parallel port driver
Nov 14 19:23:19 zod kernel: [   24.548710] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
Nov 14 19:23:19 zod kernel: [   24.567602] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
Nov 14 19:23:20 zod kernel: [   25.343093] HDMI: detected monitor PANASONIC-TV at connection type HDMI
Nov 14 19:23:20 zod kernel: [   25.343098] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
Nov 14 19:23:21 zod kernel: [   26.042065] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 14 19:23:21 zod kernel: [   26.043952] EXT4-fs (sdc1): re-mounted. Opts: commit=0
Nov 14 19:23:21 zod kernel: [   26.670901] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 14 19:23:22 zod kernel: [   26.774911] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
Nov 14 19:23:23 zod kernel: [   28.129537] eth0: no IPv6 routers present
Nov 14 19:23:31 zod kernel: [   36.450219] ISO 9660 Extensions: Microsoft Joliet Level 1
Nov 14 19:23:31 zod kernel: [   36.455991] ISOFS: changing to secondary root
Nov 14 19:26:11 zod kernel: [  196.108174] input: 00:1A:80:BC:C2:43 as /devices/virtual/input/input5

Would really like to get the supreme fx working as well as i purchased heli-x rc heli flight sim and I use a program called txppm to connect my rc remote to the computer through the mic in. Thanks.

---

### Post by CMDR:ZOD on 2010-11-15
Ok so I got alsa to finally recognize my supreme fx x-fi soundcard and it appears to work properly by adding this line in /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel probe_mask=0x1FF model=6stack-digout


New issue: This breaks alsa support for the Nvidia gtx 480 HDMI audio. Now if I run this command: $ cat /proc/asound/card1/codec#*  , all 4 audio (cards?) show up instead of just the one when hdmi audio was working. Before the supreme fx worked, the first audio card with the hdmi out was the default card. Now the supreme fx is default and i think this might be the reason why hdmi audio broke when the supreme fx is finally recognized. I tried to set defaults in alsa-base.conf but the issue is every soundcard I have uses the same codec (snd-hda-intel) and I have no way of setting default cards because of this. Please help with this. I will post an update as soon as I find a fix. I am currently looking at a possible .asoundrc file, but I will update soon with results. Thanks

---

### Post by CMDR:ZOD on 2010-11-15
Well I tried kernel 2.6.22 with the latest alsa code from ppa and with that line that used to work on 2.6.35-22 causes many,many errors and will not load the x-fi anymore. I am ready to call this a bug. Here is a post of part of my kern.log:
```

Nov 15 18:19:49 zod kernel: [   16.081616] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 15 18:19:49 zod kernel: [   16.081618] hda_intel: codec_mask forced to 0x2
Nov 15 18:19:49 zod kernel: [   16.081651]   alloc irq_desc for 75 on node -1
Nov 15 18:19:49 zod kernel: [   16.081652]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   16.081658] HDA Intel 0000:00:1b.0: irq 75 for MSI/MSI-X
Nov 15 18:19:49 zod kernel: [   16.081677] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   16.081680] ALSA hda_intel.c:2556: chipset global capabilities = 0x4401
Nov 15 18:19:49 zod kernel: [   16.576133] nvidia: module license 'NVIDIA' taints kernel.
Nov 15 18:19:49 zod kernel: [   16.576138] Disabling lock debugging due to kernel taint
Nov 15 18:19:49 zod kernel: [   16.974558]   alloc irq_desc for 24 on node -1
Nov 15 18:19:49 zod kernel: [   16.974560]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   16.974565] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
Nov 15 18:19:49 zod kernel: [   16.974570] nvidia 0000:02:00.0: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   16.974573] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Nov 15 18:19:49 zod kernel: [   16.974574] vgaarb: transferring owner from PCI:0000:02:00.0 to PCI:0000:04:00.0
Nov 15 18:19:49 zod kernel: [   16.974645] nvidia 0000:03:00.0: enabling device (0000 -> 0003)
Nov 15 18:19:49 zod kernel: [   16.974647]   alloc irq_desc for 30 on node -1
Nov 15 18:19:49 zod kernel: [   16.974648]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   16.974652] nvidia 0000:03:00.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
Nov 15 18:19:49 zod kernel: [   16.974656] nvidia 0000:03:00.0: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   16.974661] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=none
Nov 15 18:19:49 zod kernel: [   16.974710] nvidia 0000:04:00.0: enabling device (0000 -> 0003)
Nov 15 18:19:49 zod kernel: [   16.974712]   alloc irq_desc for 32 on node -1
Nov 15 18:19:49 zod kernel: [   16.974713]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   16.974716] nvidia 0000:04:00.0: PCI INT A -> GSI 32 (level, low) -> IRQ 32
Nov 15 18:19:49 zod kernel: [   16.974720] nvidia 0000:04:00.0: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   16.974725] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=none
Nov 15 18:19:49 zod kernel: [   16.974784] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.21  Thu Nov  4 20:24:24 PDT 2010
Nov 15 18:19:49 zod kernel: [   17.112020] ALSA hda_intel.c:707: azx_get_response timeout, polling the codec once: last cmd=0x100f0000
Nov 15 18:19:49 zod kernel: [   18.114513] ALSA hda_intel.c:707: azx_get_response timeout, polling the codec once: last cmd=0x100f0000
Nov 15 18:19:49 zod kernel: [   19.116571] ALSA hda_intel.c:717: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
Nov 15 18:19:49 zod kernel: [   19.982393] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input4
Nov 15 18:19:49 zod kernel: [   20.118529] ALSA hda_intel.c:725: No response from codec, disabling MSI: last cmd=0x100f0000
Nov 15 18:19:49 zod kernel: [   21.120541] ALSA hda_intel.c:1430: Codec #1 probe error; disabling it...
Nov 15 18:19:49 zod kernel: [   21.152070] ALSA hda_intel.c:914: codec_mask = 0x1
Nov 15 18:19:49 zod kernel: [   21.152075] ALSA hda_intel.c:1457: no codecs initialized
Nov 15 18:19:49 zod kernel: [   21.152285] HDA Intel 0000:00:1b.0: PCI INT A disabled
Nov 15 18:19:49 zod kernel: [   21.152310]   alloc irq_desc for 34 on node -1
Nov 15 18:19:49 zod kernel: [   21.152311]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   21.152316] HDA Intel 0000:02:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
Nov 15 18:19:49 zod kernel: [   21.152318] hda_intel: Disable MSI for Nvidia chipset
Nov 15 18:19:49 zod kernel: [   21.152319] hda_intel: codec_mask forced to 0x2
Nov 15 18:19:49 zod kernel: [   21.152340] HDA Intel 0000:02:00.1: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   21.152343] ALSA hda_intel.c:2556: chipset global capabilities = 0x2403
Nov 15 18:19:49 zod kernel: [   21.184010] ALSA hda_intel.c:1352: codec #1 probed OK
Nov 15 18:19:49 zod kernel: [   21.523478]   alloc irq_desc for 37 on node -1
Nov 15 18:19:49 zod kernel: [   21.523480]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   21.523485] HDA Intel 0000:03:00.1: PCI INT B -> GSI 37 (level, low) -> IRQ 37
Nov 15 18:19:49 zod kernel: [   21.523487] hda_intel: Disable MSI for Nvidia chipset
Nov 15 18:19:49 zod kernel: [   21.523512] HDA Intel 0000:03:00.1: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   21.523515] ALSA hda_intel.c:2556: chipset global capabilities = 0x2403
Nov 15 18:19:49 zod kernel: [   21.547292] ALSA hda_intel.c:914: codec_mask = 0xf
Nov 15 18:19:49 zod kernel: [   21.555256] ALSA hda_intel.c:1352: codec #0 probed OK
Nov 15 18:19:49 zod kernel: [   21.563243] ALSA hda_intel.c:1352: codec #1 probed OK
Nov 15 18:19:49 zod kernel: [   21.571230] ALSA hda_intel.c:1352: codec #2 probed OK
Nov 15 18:19:49 zod kernel: [   21.579235] ALSA hda_intel.c:1352: codec #3 probed OK
Nov 15 18:19:49 zod kernel: [   22.377855]   alloc irq_desc for 42 on node -1
Nov 15 18:19:49 zod kernel: [   22.377856]   alloc kstat_irqs on node -1
Nov 15 18:19:49 zod kernel: [   22.377861] HDA Intel 0000:04:00.1: PCI INT B -> GSI 42 (level, low) -> IRQ 42
Nov 15 18:19:49 zod kernel: [   22.377862] hda_intel: Disable MSI for Nvidia chipset
Nov 15 18:19:49 zod kernel: [   22.377881] HDA Intel 0000:04:00.1: setting latency timer to 64
Nov 15 18:19:49 zod kernel: [   22.377885] ALSA hda_intel.c:2556: chipset global capabilities = 0x2403
Nov 15 18:19:49 zod kernel: [   22.402075] ALSA hda_intel.c:914: codec_mask = 0xf
Nov 15 18:19:49 zod kernel: [   22.410066] ALSA hda_intel.c:1352: codec #0 probed OK
Nov 15 18:19:49 zod kernel: [   22.418072] ALSA hda_intel.c:1352: codec #1 probed OK
Nov 15 18:19:49 zod kernel: [   22.426035] ALSA hda_intel.c:1352: codec #2 probed OK
Nov 15 18:19:49 zod kernel: [   22.434041] ALSA hda_intel.c:1352: codec #3 probed OK
Nov 15 18:19:49 zod kernel: [   25.145960] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
Nov 15 18:19:49 zod kernel: [   25.146164] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Nov 15 18:19:49 zod kernel: [   25.283340] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
Nov 15 18:19:49 zod kernel: [   25.330447] type=1400 audit(1289870389.650:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1272 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.330555] type=1400 audit(1289870389.650:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1277 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.330737] type=1400 audit(1289870389.650:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1273 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.331077] type=1400 audit(1289870389.650:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1273 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.331265] type=1400 audit(1289870389.650:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1273 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.331443] type=1400 audit(1289870389.650:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1276 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.331981] type=1400 audit(1289870389.650:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1276 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.334202] type=1400 audit(1289870389.654:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1274 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.338480] type=1400 audit(1289870389.658:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1274 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.341164] type=1400 audit(1289870389.662:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1274 comm="apparmor_parser"
Nov 15 18:19:49 zod kernel: [   25.355347] sky2 0000:07:00.0: eth0: enabling interface
Nov 15 18:19:49 zod kernel: [   25.355460] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 15 18:19:49 zod kernel: [   25.359329] sky2 0000:05:00.0: eth1: enabling interface
Nov 15 18:19:49 zod kernel: [   25.359438] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov 15 18:19:49 zod kernel: [   25.387623] ppdev: user-space parallel port driver
Nov 15 18:19:51 zod kernel: [   26.921415] Bluetooth: L2CAP ver 2.14
Nov 15 18:19:51 zod kernel: [   26.921417] Bluetooth: L2CAP socket layer initialized
Nov 15 18:19:51 zod kernel: [   26.968988] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 15 18:19:51 zod kernel: [   26.968990] Bluetooth: BNEP filters: protocol multicast
Nov 15 18:19:51 zod kernel: [   26.972401] Bluetooth: SCO (Voice Link) ver 0.6
Nov 15 18:19:51 zod kernel: [   26.972403] Bluetooth: SCO socket layer initialized
Nov 15 18:19:51 zod kernel: [   27.035563] sky2 0000:07:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov 15 18:19:51 zod kernel: [   27.035676] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 15 18:19:51 zod kernel: [   27.534615] Bluetooth: RFCOMM TTY layer initialized
Nov 15 18:19:51 zod kernel: [   27.534619] Bluetooth: RFCOMM socket layer initialized
Nov 15 18:19:51 zod kernel: [   27.534620] Bluetooth: RFCOMM ver 1.11
Nov 15 18:19:52 zod kernel: [   27.794209] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 15 18:19:52 zod kernel: [   27.813003] EXT4-fs (sdc1): re-mounted. Opts: commit=0
Nov 15 18:19:52 zod kernel: [   28.392629] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
Nov 15 18:19:52 zod kernel: [   28.411578] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
Nov 15 18:19:52 zod kernel: [   28.418127] HDMI: sink_present = 1, eld_valid = 1
Nov 15 18:19:53 zod kernel: [   28.981900] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:19:53 zod kernel: [   29.192087] HDMI: detected monitor PANASONIC-TV at connection type HDMI
Nov 15 18:19:53 zod kernel: [   29.192093] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
Nov 15 18:19:53 zod kernel: [   29.208056] ALSA patch_hdmi.c:664: hdmi_setup_audio_infoframe: cvt=4 pin=5 channels=2
Nov 15 18:19:53 zod kernel: [   29.216034] HDMI: ASP channel 0 => slot 0
Nov 15 18:19:53 zod kernel: [   29.224023] HDMI: ASP channel 1 => slot 1
Nov 15 18:19:53 zod kernel: [   29.231985] HDMI: ASP channel 15 => slot 2
Nov 15 18:19:53 zod kernel: [   29.239987] HDMI: ASP channel 15 => slot 3
Nov 15 18:19:53 zod kernel: [   29.247982] HDMI: ASP channel 15 => slot 4
Nov 15 18:19:53 zod kernel: [   29.255963] HDMI: ASP channel 15 => slot 5
Nov 15 18:19:53 zod kernel: [   29.263951] HDMI: ASP channel 15 => slot 6
Nov 15 18:19:53 zod kernel: [   29.271924] HDMI: ASP channel 15 => slot 7
Nov 15 18:19:53 zod kernel: [   29.279913] HDMI: ELD buf size is 95
Nov 15 18:19:53 zod kernel: [   29.287896] HDMI: DIP GP[0] buf size is 23
Nov 15 18:19:53 zod kernel: [   29.295865] HDMI: DIP GP[1] buf size is 23
Nov 15 18:19:53 zod kernel: [   29.303868] HDMI: DIP GP[2] buf size is 23
Nov 15 18:19:53 zod kernel: [   29.311850] HDMI: DIP GP[3] buf size is 23
Nov 15 18:19:53 zod kernel: [   29.319832] HDMI: DIP GP[4] buf size is 0
Nov 15 18:19:53 zod kernel: [   29.327815] HDMI: DIP GP[5] buf size is 0
Nov 15 18:19:53 zod kernel: [   29.335802] HDMI: DIP GP[6] buf size is 0
Nov 15 18:19:53 zod kernel: [   29.343786] HDMI: DIP GP[7] buf size is 0
Nov 15 18:19:53 zod kernel: [   29.351773] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:53 zod kernel: [   29.351779] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:53 zod kernel: [   29.375768] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:19:53 zod kernel: [   29.471561] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:53 zod kernel: [   29.471566] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:53 zod kernel: [   29.472098] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:53 zod kernel: [   29.472213] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:53 zod kernel: [   29.473853] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:19:53 zod kernel: [   29.571611] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:53 zod kernel: [   29.571616] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:53 zod kernel: [   29.571670] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.667193] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.667198] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.677295] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.691362] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.691368] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.715391] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.731264] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.731269] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.731787] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:54 zod kernel: [   29.731897] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:54 zod kernel: [   29.733377] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.746977] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.746982] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.747017] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.762963] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.762968] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.773191] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.774975] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 15 18:19:54 zod kernel: [   29.776500] EXT4-fs (sdc1): re-mounted. Opts: commit=0
Nov 15 18:19:54 zod kernel: [   29.787843] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.787848] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.811806] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.827771] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.827776] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.828263] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:54 zod kernel: [   29.828396] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:54 zod kernel: [   29.829710] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.843735] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.843741] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.843786] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.859696] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:19:54 zod kernel: [   29.859702] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:19:54 zod kernel: [   29.952195] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 15 18:19:54 zod kernel: [   30.048643] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
Nov 15 18:19:59 zod kernel: [   34.867283] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:59 zod kernel: [   34.867306] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:59 zod kernel: [   34.867669] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:59 zod kernel: [   34.867687] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:59 zod kernel: [   34.868126] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:19:59 zod kernel: [   34.868220] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:01 zod kernel: [   37.229190] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.324178] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:01 zod kernel: [   37.324184] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.324241] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.421849] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:01 zod kernel: [   37.421853] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.422578] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:01 zod kernel: [   37.422639] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:01 zod kernel: [   37.424408] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.444323] eth0: no IPv6 routers present
Nov 15 18:20:01 zod kernel: [   37.519640] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:01 zod kernel: [   37.519643] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.519686] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.616402] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:01 zod kernel: [   37.616407] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:01 zod kernel: [   37.630084] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.645081] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.645085] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.645138] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.660047] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.660052] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.660588] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:02 zod kernel: [   37.660612] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:02 zod kernel: [   37.661961] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.679741] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.679745] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.679781] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.695702] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.695706] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.711048] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.724132] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.724136] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.724190] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.740093] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.740098] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.740860] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:02 zod kernel: [   37.740887] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:02 zod kernel: [   37.742676] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.756053] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.756057] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.756108] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:02 zod kernel: [   37.772011] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:02 zod kernel: [   37.772015] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:02 zod kernel: [   38.110257] ISO 9660 Extensions: Microsoft Joliet Level 1
Nov 15 18:20:02 zod kernel: [   38.153315] ISOFS: changing to secondary root
Nov 15 18:20:07 zod kernel: [   42.786051] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:07 zod kernel: [   42.786086] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:07 zod kernel: [   42.786500] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:07 zod kernel: [   42.786519] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:07 zod kernel: [   42.786921] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:07 zod kernel: [   42.786950] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:20:52 zod kernel: [   88.141538] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:52 zod kernel: [   88.154346] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:52 zod kernel: [   88.154352] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:20:52 zod kernel: [   88.154406] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:20:52 zod kernel: [   88.170307] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:20:52 zod kernel: [   88.170313] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:21:01 zod kernel: [   97.382028] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:21:01 zod kernel: [   97.382063] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:21:02 zod kernel: [   97.531412] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:21:02 zod kernel: [   97.626599] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:21:02 zod kernel: [   97.626605] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:21:02 zod kernel: [   97.626648] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:21:02 zod kernel: [   97.722397] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:21:02 zod kernel: [   97.722403] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:21:25 zod kernel: [  120.701786] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:21:25 zod kernel: [  120.701830] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:03 zod kernel: [  158.909106] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:03 zod kernel: [  159.003523] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:03 zod kernel: [  159.003530] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:03 zod kernel: [  159.003573] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:03 zod kernel: [  159.098155] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:03 zod kernel: [  159.098160] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:08 zod kernel: [  164.102238] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:08 zod kernel: [  164.102266] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:26 zod kernel: [  181.967649] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:26 zod kernel: [  182.062326] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:26 zod kernel: [  182.062334] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:26 zod kernel: [  182.062388] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:26 zod kernel: [  182.158093] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:26 zod kernel: [  182.158097] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:39 zod kernel: [  194.695725] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:39 zod kernel: [  194.709934] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:39 zod kernel: [  194.709939] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:39 zod kernel: [  194.709988] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:39 zod kernel: [  194.729637] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:39 zod kernel: [  194.729642] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:44 zod kernel: [  199.682830] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:44 zod kernel: [  199.682869] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:44 zod kernel: [  200.217160] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:44 zod kernel: [  200.233215] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:44 zod kernel: [  200.233220] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:44 zod kernel: [  200.233273] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:45 zod kernel: [  200.248266] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:45 zod kernel: [  200.248272] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:47 zod kernel: [  202.882226] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:47 zod kernel: [  202.978404] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:47 zod kernel: [  202.978412] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:47 zod kernel: [  202.978462] ALSA hda_intel.c:1676: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Nov 15 18:22:47 zod kernel: [  203.072950] ALSA patch_hdmi.c:788: hdmi_setup_stream: NID=0x5, pinctl=0x40
Nov 15 18:22:47 zod kernel: [  203.072955] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
Nov 15 18:22:49 zod kernel: [  205.205030] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:49 zod kernel: [  205.205065] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:52 zod kernel: [  207.870927] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:22:52 zod kernel: [  207.870964] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:23:11 zod kernel: [  226.527592] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
Nov 15 18:23:11 zod kernel: [  226.527639] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
```

---

### Post by Yellow Pasque on 2010-11-15
2.6.22? Lol

---

### Post by belrik on 2012-12-16
Thanks - this also fixes sound for the Asus SupremeFx adapter in 12.10 where is still cuts out at random.

Added the following to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel probe_mask=0x1FF model=6stack-digout

Could really use a mention in the wiki, will see if I can contribute there.

---

### Post by overdrank on 2012-12-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

