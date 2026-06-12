---
title: "zoneminder problems"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by JanSwe on 2007-07-29
Hi,
I downloaded and installed zoneminder acording:
[http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04](http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04)

and run the mysql part of the installation guide. I can start zoneminder and setup a monitor bur don't get any pictures.

In syslog I can see:
Jul 29 16:16:47 ppmitx1 zmdc[5401]: INF [Starting pending process, zmc -d /dev/video0] 
Jul 29 16:16:47 ppmitx1 zmdc[5401]: INF ['zmc -d /dev/video0' starting at 07/07/29 16:16:47, pid = 6217] 
Jul 29 16:16:47 ppmitx1 zmdc[6217]: INF ['zmc -d /dev/video0' started at 07/07/29 16:16:47] 
Jul 29 16:16:47 ppmitx1 zmc_dvideo0[6217]: INF [Debug Level = 0, Debug Log = <none>]
Jul 29 16:16:47 ppmitx1 zmc_dvideo0[6217]: ERR [Failed to setup memory: Invalid argument]
Jul 29 16:16:47 ppmitx1 zmdc[5401]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 255] 

I can get a live picture from my camera on composite with vlc media player using pvr tab cahnnel 2 but not with xawtv.

xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Hauppauge WinTV PVR-150
    flags:  capture tuner 

also dmesg looks ok (i think):
[   30.616000] ivtv:  ==================== START INIT IVTV ====================
[   30.616000] ivtv:  version 0.10.1 (tagged release) loading
[   30.616000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   30.616000] ivtv:  In case of problems please include the debug info between
[   30.616000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   30.616000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   30.616000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   30.616000] ACPI: PCI Interrupt 0000:00:14.0[A] -> GSI 17 (level, low) -> IRQ 16
[   30.616000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   31.376000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   31.592000] ivtv0: Encoder revision: 0x02050032
[   31.592000] ivtv0: Recommended firmware version is 0x02060039.
[   31.684000] tveeprom 1-0050: Hauppauge model 26559, rev F189, serial# 9913033
[   31.684000] tveeprom 1-0050: tuner model is TCL MFPE05 2 (idx 89, type 38)
[   31.684000] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   31.684000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   31.684000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   31.684000] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   31.684000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   31.736000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   31.736000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   31.744000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   31.820000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   36.948000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   37.100000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   37.172000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   37.172000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   37.172000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   37.172000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   37.176000] ivtv0: Registered device radio0 for encoder radio
[   37.176000] tuner 1-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   37.580000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   37.580000] ivtv:  ====================  END INIT IVTV  ====================


starting xawtc in a console produces the following output:

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
WARNING: v4l-conf is compiled without DGA support.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

any idea on what is wrong and what I can do?

---

