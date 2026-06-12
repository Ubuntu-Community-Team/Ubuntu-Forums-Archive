---
title: "lucid"
date: 2010-11-15
forum: Multimedia Software
---

### Post by taarhaug on 2010-11-15
Hi,

Finally succeeding in mplayer -vo vdpau at home so I thought I'd have a go at the x64 installation at the office.  mplayer fails with the following message:

Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
VDPAU capture: Enabled
vdp_imp_device_create_x11(0x2957cc0, 0, -, -)
VDPAU nvidia: Version: NVIDIA VDPAU Driver Shared Library  260.19.12  Fri Oct  8 11:46:03 PDT 2010
VDPAU nvidia: Error detected 10 213  5
VDPAU nvidia: Backtrace:
--: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f0a7911d000] DSO load base
00: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f0a791505ad] 
01: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f0a791406ba] 
02: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f0a79125fe3] vdp_imp_device_create_x11
    -> 1
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

I think I have the latest of nvidia, libvdpau1, mplayer etc installed.

Suggestions how to proceed?

Thor

---

