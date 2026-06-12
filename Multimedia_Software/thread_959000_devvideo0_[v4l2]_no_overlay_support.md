---
title: "/dev/video0 [v4l2]: no overlay support"
date: 2008-10-26
forum: Multimedia Software
---

### Post by smaring on 2008-10-26
I'm running 8.10 (intrepid), fully updated, and I cannot seem to get my Belkin USB VideoBus II usb dongle to work.  I keep getting "no overlay support".

```

# uname -a
Linux christa-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

# xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-7-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway

# v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1280x1024, depth=24, bpp=32, bpl=5120, base=unknown
/dev/video0 [v4l2]: no overlay support

# v4l-info
...
### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "Belkin USB VideoBus II"
        type                    : 0x1 [CAPTURE]
        channels                : 2
        audios                  : 0
        maxwidth                : 320
        maxheight               : 240
        minwidth                : 48
        minheight               : 32

channels
    VIDIOCGCHAN(0)
        channel                 : 0
        name                    : "Composite Video Input"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 1
    VIDIOCGCHAN(1)
        channel                 : 1
        name                    : "S-Video Input"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 1
...

# dmesg | grep video
[    1.320310] pci 0000:01:00.0: Boot video device
[   21.539659] Linux video capture interface: v2.00
[   21.620429] USBVision[0]: registered USBVision Video device /dev/video0 [v4l2]
[   21.622113] Modules linked in: usbvision(+) videodev v4l1_compat compat_ioctl32 snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi parport_pc parport snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc button i2c_nforce2 i2c_core amd64_agp agpgart ext3 jbd mbcache usbhid hid sr_mod cdrom sd_mod crc_t10dif sg pata_acpi sata_nv ohci1394 ata_generic pata_amd sata_sil ieee1394 skge libata scsi_mod ohci_hcd ehci_hcd dock forcedeth usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse

```

I should probably also point out that my lsusb command hangs, as does xsane, not sure if that is related.

-Steve Maring

---

