---
title: "Playback freeze after a second."
date: 2014-10-28
forum: Mythbuntu
---

### Post by khPWXxF on 2014-10-28
I'm struggling here and would appreciate other opinions.

I run a combined FE/BE on my Asus M3N78-EM mobo with onboard Nvidia 8300 graphics and receive DVB-T (MPEG2 recordings) here in the UK.  I have 512MB of the total 4GB of RAM allocated in the BIOS to graphics. I treat it as a device;  I use mythwelcome  and I have frozen software updates.  I have Mythtv fixes/0.27 (v0.27.3-150-g082d5c1).  

When I loaded 14.04 back in April 2014 I requested loading of Nvidia graphics and 311 was loaded.  This was totally unstable, but stability was restored by downgrading to 304 (or so I thought):
```
sudo apt-get update
sudo apt-get install nvidia-304

```
It wasn't as stable as the previous 295 though (high cpu even with VDPAU on, interlacing visible and artefacts on the HD setup demo) but worked fine for months. 

Since 8th Oct I've had eight instances (three yesterday) of screen locking about a second or so into playback of a recording which can only be released by a reboot.
The tail of the frontend log shows this to be a buffer problem [columns with user etc removed for readability]:

```
Oct 26 12:52:30 : I CoreContext videoout_opengl.cpp:327 (SetupContext) VidOutGL: Created MythRenderOpenGL device.
Oct 26 12:52:30 : I CoreContext mythpainter_ogl.cpp:27 (MythOpenGLPainter) OpenGL painter using existing OpenGL context.
Oct 26 12:52:30 : I CoreContext mythpainter_ogl.cpp:29 (MythOpenGLPainter) OpenGL painter using existing QGLWidget.
Oct 26 12:52:30 : I CoreContext openglvideo.cpp:230 (Init) GLVid: Using custom UYVY input textures.
Oct 26 12:52:30 : I CoreContext mythplayer.cpp:1781 (InitAVSync) Player(0): Video timing method: DRM
Oct 26 12:52:30 : I CoreContext tv_play.cpp:5621 (StartPlayer) TV: Created player.
Oct 26 12:52:30 : I CoreContext tv_play.cpp:2485 (HandleStateChange) TV: Changing from None to WatchingPreRecorded
Oct 26 12:52:30 : I CoreContext tv_play.cpp:2576 (HandleStateChange) TV: Main UI disabled.
Oct 26 12:52:30 : I CoreContext tv_play.cpp:412 (StartTV) TV: Entering main playback loop.
Oct 26 12:52:53 : E Decoder mythplayer.cpp:3388 (DecoderGetFrame) Player(0): Decoder timed out waiting for free video buffers.

```

dmesg shows what looks like a clash between Nouveau and Nvidia at 15.25.  Nouveau loads first, and nvidia therefore bombs out.  I can only assume that this has been going on since April.  Here are the key bits of it:


```
[    0.000000] Linux version 3.13.0-30-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 (Ubuntu 3.13.0-30.55-generic 3.13.11.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=46afe4de-bede-4715-ba8f-0174d754c276 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
...


[   13.634991] nouveau  [  DEVICE][0000:02:00.0] BOOT0  : 0x0aa400a2
[   13.634992] nouveau  [  DEVICE][0000:02:00.0] Chipset: MCP77/MCP78 (NVAA)
[   13.634993] nouveau  [  DEVICE][0000:02:00.0] Family : NV50
[   13.635581] nouveau  [   VBIOS][0000:02:00.0] checking PRAMIN for image...
[   13.687175] nouveau  [   VBIOS][0000:02:00.0] ... appears to be valid
[   13.687176] nouveau  [   VBIOS][0000:02:00.0] using image from PRAMIN
[   13.687286] nouveau  [   VBIOS][0000:02:00.0] BIT signature found
[   13.687287] nouveau  [   VBIOS][0000:02:00.0] version 62.77.35.00.00
[   13.711610] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   13.711619] hda_intel: Disabling MSI
[   13.711644] hda-intel 0000:00:07.0: Disabling 64bit DMA
[   13.714571] nouveau  [     PFB][0000:02:00.0] RAM type: stolen system memory
[   13.714572] nouveau  [     PFB][0000:02:00.0] RAM size: 512 MiB
[   13.714573] nouveau  [     PFB][0000:02:00.0]    ZCOMP: 0 tags
[   13.718068] hda-intel 0000:00:07.0: Enable delay in RIRB handling
[   13.723439] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   13.727203] nouveau  [    VOLT][0000:02:00.0] GPU voltage: 1100000uv
[   13.755011] mceusb 5-2:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver with mce emulator interface version 1
[   13.755012] mceusb 5-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x1 active)
[   13.755557] usbcore: registered new interface driver mceusb
[  


...
[   15.002179] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[   15.073469] nouveau  [  PTHERM][0000:02:00.0] FAN control: none / external
[   15.073481] nouveau  [  PTHERM][0000:02:00.0] fan management: automatic
[   15.073484] nouveau  [  PTHERM][0000:02:00.0] internal sensor: yes
[   15.073503] nouveau  [     CLK][0000:02:00.0] 0f: core 500 MHz shader 1500 MHz vdec 500 MHz
[   15.073522] nouveau  [     CLK][0000:02:00.0] --: core 350 MHz shader 800 MHz vdec 350 MHz
[   15.079948] [TTM] Zone  kernel: Available graphics memory: 1765990 kiB
[   15.079952] [TTM] Initializing pool allocator
[   15.079956] [TTM] Initializing DMA pool allocator
[   15.079970] nouveau  [     DRM] VRAM: 512 MiB
[   15.079971] nouveau  [     DRM] GART: 1048576 MiB
[   15.079976] nouveau  [     DRM] TMDS table version 2.0
[   15.079977] nouveau  [     DRM] DCB version 4.0
[   15.079980] nouveau  [     DRM] DCB outp 00: 01000300 0000001e
[   15.079982] nouveau  [     DRM] DCB outp 01: 01011332 00020010
[   15.079984] nouveau  [     DRM] DCB conn 00: 00000000
[   15.079986] nouveau  [     DRM] DCB conn 01: 00003161
[   15.087484] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   15.087486] [drm] No driver support for vblank timestamp query.
[   15.101290] nouveau  [     DRM] MM: using M2MF for buffer copies
[   15.176121] nouveau  [     DRM] allocated 1920x1080 fb: 0x50000, bo ffff8800aa0c7400
[   15.176240] fbcon: nouveaufb (fb0) is primary device
[   15.229105] init: failsafe main process (633) killed by TERM signal
[   15.234693] Console: switching to colour frame buffer device 240x67
[   15.238242] nouveau 0000:02:00.0: fb0: nouveaufb frame buffer device
[   15.238244] nouveau 0000:02:00.0: registered panic notifier
[   15.241188] [drm] Initialized nouveau 1.1.1 20120801 for 0000:02:00.0 on minor 0
[   15.259805] nvidia: module license 'NVIDIA' taints kernel.
[   15.259811] Disabling lock debugging due to kernel taint
[   15.269415] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   15.269602] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.269780] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   15.282012] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   15.299882] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   15.299887] NVRM: This can occur when a driver such as nouveau, rivafb,
[   15.299887] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
[   15.299887] NVRM: the NVIDIA device(s).
[   15.299890] NVRM: Try unloading the conflicting kernel module (and/or
[   15.299890] NVRM: reconfigure your kernel without the conflicting
[   15.299890] NVRM: driver(s)), then try loading the NVIDIA kernel module
[   15.299890] NVRM: again.
[   15.299892] NVRM: No NVIDIA graphics adapter probed!
[   15.411962] usb 3-1: DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[   15.437643] MT2060: successfully identified (IF1 = 1223)
[   15.931754] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.931883] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   15.939519] usb 3-1: DVB: registering adapter 2 frontend 0 (DiBcom 3000MC/P)...
[   15.944664] MT2060: successfully identified (IF1 = 1241)
[   16.090527] init: avahi-cups-reload main process (734) terminated with status 1
[   16.435246] forcedeth 0000:00:0a.0: irq 41 for MSI/MSI-X
[   16.435279] forcedeth 0000:00:0a.0 eth0: MSI enabled
[   16.505291] Registered IR keymap rc-dib0700-rc5
[   16.505647] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-1/rc/rc2/input12
[   16.505715] rc2: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-1/rc/rc2
[   16.505902] dvb-usb: schedule remote query interval to 50 msecs.
[   16.505908] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   16.506501] usbcore: registered new interface driver dvb_usb_dib0700
[   16.696005] input: HDA NVidia HDMI/DP,pcm=7 Phantom as /devices/pci0000:00/0000:00:07.0/sound/card0/input21
[   16.696150] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input20
[   16.696229] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input19
[   16.696300] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input18
[   16.696369] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input17
[   16.696438] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input16
[   16.696513] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input15
[   16.696581] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input14
[   16.696651] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
[   16.781417] init: samba-ad-dc main process (749) terminated with status 1
[   17.070997] init: nvidia-prime main process (974) terminated with status 127

```

lsmod confirms that video is controlled by nouveau and there are NO references to nvidia in it.
Oddly, this is the case even when playback works.

I think I have copied all relevant logs to this incident so if there's anything missing please ask.

Two other observations which may be relevant but probably aren't:
1.  I had the 'blank screen if myth powered before tv'.  Fixed with a custom /etc/X11/xorg.conf and making it immutable - it kept vanishing.
2.  The fixes introduced in 27.1 or 27.2 to eliminate the xfce strip across top of screen do not work for me.  I have to have a work-round on frontend startup.

At this stage I'd really appreciate advice on which way to jump.  Nouveau under 14.04 is not as good as the nvidia 295 drivers were under 12.04 so I'd err towards nvidia.  
Would you use Nouveau, kill off Nouveau (how?) and use Nvidia (Which one?) or buy a more modern fanless graphics card (which?).

Phil

---

### Post by aelfric55 on 2014-10-29
Normally the nouveau module is blacklisted on machines with Nvidia drivers installed, and doesn't load. 

Installation of an NVidia graphics package on Ubuntu should have blacklisted the nouveau module automatically for you, but evidently did not do so. 

There should exist either a /etc/modprobe.d/nvidia-graphics-drivers.conf file, or a /etc/modprobe.d/blacklist.conf  

In one of these files, among all the other blacklisted things there should be the line```
blacklist nouveau
``` This line should prevent the nouveau module from loading and killing your Nvidia driver.

---

### Post by khPWXxF on 2014-10-30
Many thanks for the pointer Aelfrec55 - you are spot on.
I have two setups, one a clone of the other which I alternate when doing updates.  Oddly, the 'backup' one does have blacklisting there!

/etc/modprobe.d/nvidia-graphics-drivers.conf is a link to a link to a file with
```
 # This file was installed by nvidia-304
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_304
alias nouveau off
alias lbm-nouveau off
```

All fixed now - thanks again
Phil

---

