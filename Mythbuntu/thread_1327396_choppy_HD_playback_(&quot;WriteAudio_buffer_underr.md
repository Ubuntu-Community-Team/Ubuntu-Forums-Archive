---
title: "choppy HD playback (&quot;WriteAudio: buffer underrun&quot;) on Live TV only, prerecorded OK"
date: 2009-11-15
forum: Mythbuntu
---

### Post by twelve17 on 2009-11-15
I'm experiencing choppy HD playback ("WriteAudio: buffer underrun") when watching Live TV.  Previously recorded shows play back just fine.  I can start recording a show in progress that plays choppy on Live TV, then immediately go into the recorded programs and continue watching it with no problem.

I want to think that it's not your typical bad audio or video or performance issue, as I can play the exact same video clips once they are recorded, even as they are still being recorded as I watch them via the "recorded programs" menu.

This issue sounds like it's what's biting me, but I *think* the fix for that issue should be included in my mythtv version:

[http://svn.mythtv.org/trac/ticket/5025](http://svn.mythtv.org/trac/ticket/5025)

Is there a way to verify this?

Anyway here's the information on my setup:

mythtv version: 0.21.0+fixes21768-0ubuntu0+mythbuntu3
nvidia driver: 96.43.13
hardware: Pinnacle PCTV HD 800i, intel ICH5 audio
playback profile: XvMC with opengl OSD.
audio: pass-through to SPDIF, max channels=stereo, upsampling=passive

lspci output (partial):
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:07.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:08.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:08.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:08.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
```

My Xorg.conf (full):
```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "UseEvents"      "true"
        Option "XvmcUsesTextures" "true"  # necessary for color Chromakey OSD)
        Option "NVAGP"          "2"     # some users report 2 or 3 works better
EndSection

Section "Extensions"
     Option "Composite" "Disabled"
EndSection

```

Dmesg output related to Nvidia/AGP:
```

[    7.441838] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   32.175955] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode

```

My videos are written to an external USB drive, and the MySQL on the system drive.  When playing HD streams, my CPU is between 35 and 50%, and the external hard drive doesn't seem to be being taxed.

I'm not having much luck figuring out what the difference is when playing live tv versus prerecorded shows.

I've run "mythtv log playback" and logged playing live tv vs recorded shows to see if someone can spot a meaningful difference or hint in the log output. See attached play*.gz files.  I've removed the time stamps from both logs for easier diff'ing/meld'ing, but I wasn't able to figure it out on my own.

Any help would be highly appreciated.

Thanks,

Alex

---

