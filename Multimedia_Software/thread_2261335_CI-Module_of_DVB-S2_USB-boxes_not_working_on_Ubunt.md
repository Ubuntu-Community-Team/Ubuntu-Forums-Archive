---
title: "CI-Module of DVB-S2 USB-boxes not working on Ubuntu"
date: 2015-01-18
forum: Multimedia Software
---

### Post by wasu on 2015-01-18
Hi,

I am currently testing the following DVB-S2 USB-boxes: DVBSky S960CI, TBS 5980 CI, Terratec S7 CI on Ubuntu 10.04., 12.04., 14.04..
DVBSky S960CI and TBS 5980 CI work with the manufacturer-drivers for non-encrypted-channels, I could not get working Terratec S7 CI so far.
For testing with encrypted channels I have 2 different CI-Modules: SCM Microsystems Cryptoworks, irdeto cryptoworks.

On Ubuntu I receive non-encrypted channels, but receiving encrypted channels does not work.
I am from Austria, Europe, so I want to receive the channels ORF1, ORF2 and ORF3 on Astra 19.2..
These channels however are encrypted, so I have a ORF-digital-card which I give in the CI-Slot of the CI-Module.

On Windows 7 all 3 mentioned DVB-S2 USB-boxes work fine with the manufacturer-drivers and with both mentioned CI-modules.
This means, ORF1, ORF2 and ORF3 are received and displayed correctly on Windows 7.

But not so on Ubuntu, encrypted channels ORF1, ORF2, ORF3 are not displayed on Ubuntu 10.04., 12.04., 14.04. (while using the ORF-digital-card for decryption in the CI-Module).
Non-encrypted channels like BBC are working fine.

Can anyone tell me how to get the CI-Modules working on Ubuntu?

Here are the details:
Example-installation for the DVBSky S960CI at Ubuntu 14.04.
Installation-instructions found at: [http://www.dvbsky.net/Support_linux.html](http://www.dvbsky.net/Support_linux.html)

```
uname -a
Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

my kernel has version 3.13., so I downloaded media_build-bst-13-140619.tar.gz

```
apt-get update
apt-get upgrade
apt-get install kernel-package linux-headers-`uname -r`
tar xzvf media_build-bst-13-140619.tar.gz
cd media_build-bst-13
./v4l/build_x64.sh
make
make install
tar xzvf dvbsky-firmware.tar.gz
cd dvbsky-firmware
./copy-firmware.sh
reboot
```

Checking via dmesg if device is connected successfully via USB:
Everything seems ok.

```
dmesg | grep -i dvb
[   76.964262] dvbsky_identify_state, build on Jan 17 2015 20:45:04(),delay=0
[   76.964304] usbcore: registered new interface driver dvb_usb_dvbsky
[   77.139759] usb 2-1.1: dvb_usb_v2: found a 'DVBSky S960CI' in warm state
[   77.139901] usb 2-1.1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   77.139945] DVB: registering new adapter (DVBSky S960CI)
[   77.141396] dvbsky_usb MAC address=00:18:42:54:96:0c
[   77.141402] usb 2-1.1: dvb_usb_v2: MAC address: 00:18:42:54:96:0c
[   77.212394] m88ds3103_load_firmware: Waiting for firmware upload (dvb-fe-ds3103.fw)...
[   78.338760] usb 2-1.1: DVB: registering adapter 0 frontend 0 (Montage DS3103/TS2022)...
[   78.369010] Registered IR keymap rc-dvbsky
[   78.369226] input: DVBSky S960CI as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rc/rc0/input19
[   78.369342] rc0: DVBSky S960CI as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rc/rc0
[   78.369349] usb 2-1.1: dvb_usb_v2: schedule remote query interval to 300 msecs
[   78.369355] usb 2-1.1: dvb_usb_v2: 'DVBSky S960CI' successfully initialized and connected
[   86.492006] dvb_ca adapter 0: DVB CAM detected and initialised successfully
```

Zapping to channel BBC via szap:

```
szap -r -c channels.conf "BBC World(BBC)"
reading channels from file 'channels.conf'
zapping to 588 'BBC World(BBC)':
sat 0, frequency = 10743 MHz H, symbolrate 22000000, vpid = 0x00a3, apid = 0x005c sid = 0x2742
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
Version: 5.10    FE_CAN { DVB-S + DVB-S2 }
status 1f | signal 8944 | snr 244c | ber 00000000 | unc 0000000b | FE_HAS_LOCK
status 1f | signal 8944 | snr 244c | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8944 | snr 273e | ber 00000000 | unc 00000000 | FE_HAS_LOCK
...
```

Playing BBC via mplayer2:

```
mplayer /dev/dvb/adapter0/dvr0
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Playing /dev/dvb/adapter0/dvr0.
Detected file format: MPEG-TS (MPEG-2 Transport Stream) (libavformat)
[mpeg2video @ 0x7f0cd17fdb00]mpeg_decode_postinit() failure
[mpeg2video @ 0x7f0cd17fdb00]mpeg_decode_postinit() failure
[mpeg2video @ 0x7f0cd17fdb00]mpeg_decode_postinit() failure
[mpegts @ 0x7f0cd1030600]max_analyze_duration reached
[mpegts @ 0x7f0cd1030600]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (mpeg2video), -vid 0
[lavf] stream 1: audio (mp2), -aid 0
Load subtitles in /dev/dvb/adapter0/
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[ass] auto-open
Selected video codec: MPEG-2 video [libavcodec]
Selected audio codec: MPEG 1.0/2.0/2.5 layers I, II, III [mpg123]
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg2video @ 0x7f0cd17fdb00]warning: first frame is no keyframe
VIDEO:  720x576  25.000 fps  15000.0 kbps (1875.0 kB/s)
Aspect ratio is 1.78:1 - scaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12
A:4526.0 V:4526.0 A-V: -0.026 ct:  0.000   0/  0 ??% ??% ??,?% 0 0
Decreasing video pts: 4525.926233 < 4526.006233
A:4526.0 V:4526.0 A-V: -0.022 ct:  0.000   0/  0 ??% ??% ??,?% 0 0
Decreasing video pts: 4525.966233 < 4526.006233
A:4530.6 V:4530.6 A-V: -0.000 ct: -0.024   0/  0  6%  1%  0.5% 0 0
```

The mplayer window opens and BBC is displayed correctly.

Now zapping to encrypted ORF1 channel while using the ORF-digital-card for decryption in the CI-Module.

```
szap -r -c channels.conf "ORF1(ORF)"
reading channels from file 'channels.conf'
zapping to 252 'ORF1(ORF)':
sat 0, frequency = 12692 MHz H, symbolrate 22000000, vpid = 0x00a0, apid = 0x00a3 sid = 0x32c9
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
Version: 5.10    FE_CAN { DVB-S + DVB-S2 }
status 1f | signal 8e35 | snr d026 | ber 00000000 | unc 0000000b | FE_HAS_LOCK
status 1f | signal 8e35 | snr d026 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8e35 | snr d026 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
...
```

Playing ORF1 via mplayer2:

```
mplayer /dev/dvb/adapter0/dvr0
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Playing /dev/dvb/adapter0/dvr0.
Detected file format: MPEG-TS (MPEG-2 Transport Stream) (libavformat)
```

Now nothing happens.
No mplayer-window is opend, ORF1 is not displayed.

Can anyone help me here with getting the CI-Modules to work?

Has anyone running a DVB-S2 USB-box with CI-module on Ubuntu successfully and can display encrypted channels?

Which DVB-S2 USB-Box? Which Ubuntu-Version? How was Driver-Installation?

Any help appreciated.

---

### Post by Rumen_Krastev on 2015-02-05
I'm also interested of the solution, any update?

---

### Post by Rumen_Krastev on 2015-02-26
Try to turn the smart card (not the module) up side down, strange or not this was the problem in my case.. under Linux it doesn't show the error of the cam, but under Windows it shows "error reading smart card" ;)

---

