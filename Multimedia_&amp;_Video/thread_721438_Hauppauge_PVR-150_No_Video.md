---
title: "Hauppauge PVR-150 No Video"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by _seanc_ on 2008-03-11
I've been struggling for a while now and wearing out the patience of my local user group. I hope someone here can help.

I have my Hauppauge PVR-150 connected to an antenna, and I have managed to get as far as tuning it into a channel:

$ ivtv-tune -c 49 -t southafrica -d /dev/video0
/dev/video0: 695.250 MHz
$ vlc pvr:// :pvr-device="/dev/video0"
VLC media player 0.8.6c Janus

... but I get audio only -- no picture apart from spots on a black background.

I'm told this means I'm not using PAL, but I can't figure out how to change that.

Based on similar posts, here are the relevant details:

$ lsmod | grep ivtv
ivtv                  134928  0
i2c_algo_bit            7428  3 cx88xx,bttv,ivtv
cx2341x                13316  1 ivtv
tveeprom               16784  3 cx88xx,bttv,ivtv
videodev               29312  4 cx8800,cx88xx,bttv,ivtv
v4l2_common            18432  9 cx8800,cx88xx,bttv,wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  3 bttv,ivtv,videodev
i2c_core               26112  10 cx88xx,bttv,lirc_i2c,wm8775,cx25840,tuner,ivtv,nvidia,i2c_algo_bit,tveeprom

$ dmesg
...
[   32.499797] ivtv:  ==================== START INIT IVTV ====================
[   32.499800] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   32.499850] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   32.499976] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.611495] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   32.611513] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.818707] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   33.182527] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4106265040 bytes)
[   33.394483] ivtv0: Encoder revision: 0x02060039
[   33.455704] tveeprom 0-0050: The eeprom says no radio is present, but the tuner type
[   33.455707] tveeprom 0-0050: indicates otherwise. I will assume that radio is present.
[   33.455710] tveeprom 0-0050: Hauppauge model 26139, rev F1A5, serial# 10230905
[   33.455712] tveeprom 0-0050: tuner model is TCL MPE05-2 (idx 105, type 38)
[   33.455714] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   33.455716] tveeprom 0-0050: audio processor is CX25842 (idx 36)
[   33.455718] tveeprom 0-0050: decoder processor is CX25842 (idx 29)
[   33.455720] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
[   33.455723] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   33.455724] ivtv0: reopen i2c bus for IR-blaster support
[   33.498231] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   33.498250] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   33.533361] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   33.724120] cx25840 0-0044: cx25842-24 found @ 0x88 (ivtv i2c driver #0)
[   37.480741] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   37.584972] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   37.635234] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   37.958538] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   37.958675] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   37.958820] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   37.958876] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   37.959064] ivtv0: Registered device radio0 for encoder radio
[   37.988162] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   37.988273] ivtv:  ====================  END INIT IVTV  ====================
...

$ dpkg -l ivtv*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  ivtv-firmware  0.20070217     Firmware used by the IVTV project
un  ivtv-firmware- <none>         (no description available)
un  ivtv-modules   <none>         (no description available)
ii  ivtv-utils     1.0.2-2        utilities for use with the ivtv kernel drive

$ v4l2-ctl -I
Video input : 0 (Tuner 1)

$ v4l2-ctl -n
ioctl: VIDIOC_ENUMINPUT
        Input   : 0
        Name    : Tuner 1
        Type    : 0x00000001
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x000000000000000F ( PAL )
        Status  : 0

        Input   : 1
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 3
        Name    : S-Video 2
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : Composite 2
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0


I'd appreciate any help you can give.

Thank you,
Sean

---

### Post by _seanc_ on 2008-03-12
I found something that I thought might be useful on the FAQ at: ivtv.writeme.ch/tiki-view_faq.php

[INDENT]Q: I'm in a PAL/SECAM country, how do I capture?
A: Ivtv fully supports PAL/SECAM. When the module loads it should automatically switch to the PAL standard if you have a PAL tuner.
You can specify the ivtv_std=2 option when loading the ivtv module if it's not picked up as expected.

You can also use the ivtvctl app from the /util directory to change it, if it's not picked up correctly:

ivtvctl -u 0xff

You may also need to change to the full PAL resolution:

ivtvctl -f width=720,height=576

If you need to change input to the tuner you can do so by:

ivtvctl -p x where x is a number in the range 0-9, which correspond to the different inputs (Svideo, composite, tuner, but it differs from card to card. test them all to be sure).[/INDENT]

Unfortunately I don't have those options available in ivtvctl:

$ sudo ivtvctl -f width=720,height=576
ivtvctl: invalid option -- f
Unknown argument `width=720,height=576'
Usage:
  -d, --device <dev> use device <dev> instead of /dev/video0
  -h, --help         display this help message
  -K, --passthrough <mode>
                     set passthrough mode: 1 = on, 0 = off [IVTV_IOC_PASSTHROUGH]
  --get-yuv-mode     display the current yuv mode
  --set-yuv-mode mode=<mode>
                     set the current yuv mode:
                     mode 0: interlaced (top transmitted first)
                     mode 1: interlaced (bottom transmitted first)
                     mode 2: progressive
                     mode 3: auto
  --reset-ir         reset the infrared receiver [VIDIOC_INT_RESET]
  --version          shows the version number of this utility.
                     It should match the driver version.

Expert options:
  -D, --set-debug <level>
                     set the module debug variable
                      1: WARN   2: INFO  4: API   8: DMA  16: IOCTL
                     32: I2C   64: IRQ 128: DEC 256: YUV 512: High Volume msgs
  -E, --end-gop      capture last GOP [IVTV_IOC_S_GOP_END]
  -e, --get-debug    query the module debug variable
  -I, --list-gpio
                     show GPIO input/direction/output bits
  -i, --set-gpio [dir=<dir>,]val=<val>
                     set GPIO direction bits to <dir> and set output to <val>
  -k, --sync         test vsync's capabilities [VIDEO_GET_EVENT]
  -v, --audio-route=input=<in>,output=<out>
                     set the audio input/output routing [VIDIOC_INT_S_AUDIO_ROUTING]


I'm still stuck!

Sean

---

