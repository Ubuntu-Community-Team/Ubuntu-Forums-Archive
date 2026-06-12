---
title: "bttv, bt878, and zvbi failing"
date: 2011-01-07
forum: Multimedia Software
---

### Post by ian_d on 2011-01-07
I'm having a problem getting my (rather old, really) Hauppauge WinTV cards working correctly in Ubuntu 10.10. It's kind of a weird situation, though. The machine is effectively running headless because I'm not particularly interested in the video feed but instead in the closed captions. This same card worked correctly with the old v4l drivers in kernel 2.4, but I haven't attempted to use it since then. (And there's two other tv cards of the same make in the machine, with the same behavior.)

Here's the message I get when using zvbi-ntsc-cc:

```
# zvbi-ntsc-cc -d /dev/vbi0 -c -v
Try to open V4L2 0.20 VBI device, libzvbi interface rev.
  $Id: io-v4l2.c,v 1.37 2008/02/19 00:35:20 mschimek Exp $
Opened /dev/vbi0
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Try to open V4L2 2.6 VBI device, libzvbi interface rev.
  $Id: io-v4l2k.c,v 1.49 2008/02/19 00:35:20 mschimek Exp $.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Opened /dev/vbi0.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: /dev/vbi0 (BT878 video (Hauppauge (bt878))) is a v4l2 vbi device,
driver bttv, version 0x00000912.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Using streaming interface.
libzvbi:io-v4l2k:v4l2_get_videostd: Current scanning system is 625.
libzvbi:io-v4l2k:v4l2_update_services: Querying current vbi parameters...
libzvbi:io-v4l2k:v4l2_update_services: ...success.
libzvbi:print_vfmt: VBI capture parameters supported: 
libzvbi:io-v4l2k:v4l2_update_services: Attempt to set vbi capture parameters.
libzvbi:sampling_par:_vbi_sampling_par_from_services_log: Service 0x00000020 (Closed Caption 525, field 1) requires videostd_set 0x2, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_from_services_log: Service 0x00000040 (Closed Caption 525, field 2) requires videostd_set 0x2, have 0x0.
libzvbi:io-v4l2k:v4l2_update_services: Will capture services 0x00000000, added 0x0 commit=1.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Failed with errno 22, errmsg 'Sorry, /dev/vbi0 (BT878 video (Hauppauge (bt878))) cannot capture any of the requested data services with scanning 625.'.
Cannot capture vbi data with v4l2 interface:
Sorry, /dev/vbi0 (BT878 video (Hauppauge (bt878))) cannot capture any of the requested data services with scanning 625.
Will try v4l.
libzvbi: Try to open v4l vbi device, libzvbi interface rev.
  $Id: io-v4l.c,v 1.38 2008/02/24 14:17:28 mschimek Exp $
libzvbi: Opened /dev/vbi0
libzvbi: Driver name 'BT878 video (Hauppauge (bt878))'
libzvbi: /dev/vbi0 (BT878 video (Hauppauge (bt878))) is a v4l vbi device
libzvbi: Hinted video standard 525, guessed 525
libzvbi: Driver supports VIDIOCGVBIFMT, guessed videostandard 625
VBI capture parameters supported: format 0000000c, 35468950 Hz, 2048 bpl, F1 7+16, F2 320+16, flags 00000000
libzvbi: Driver does support VIDIOCSVBIFMT
libzvbi: Attempt to set vbi capture parameters
VBI capture parameters granted: format 0000000c, 35468950 Hz, 2048 bpl, F1 7+1, F2 320+1, flags 00000000
libzvbi: Accept current vbi parameters
libzvbi: Nyquist check passed
libzvbi: Request decoding of services 0x00000060, strict level 1
libzvbi: Will capture services 0x00000000, added 0x0 commit:1
Cannot capture vbi data with v4l interface:
Sorry, /dev/vbi0 (BT878 video (Hauppauge (bt878))) cannot capture any of the requested data services.

```The behavior of the v4lctl settings is also strange. I can setnorm, setfreqtab, setchannel all correctly, but after running a test capture with mencoder the norm is switched from NTSC (which I set) to PAL-DK. The captured output is also all static.
```
# v4lctl -c /dev/video0 list
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | PAL-DK  | NTSC    | NTSC NTSC-M NTSC-M-JP NTSC-M-KR PAL PAL-BG PAL-H PAL-I PAL-DK PAL-M PAL-N PAL-Nc PAL-60 SECAM SECAM-B SECAM-G
input      | choice | Televis | Televis | Television Composite1 S-Video Composite3
audio mode | choice | mono    | mono    | mono stereo lang1 lang2
bright     | int    |   32768 |   32768 | range is 0 => 65535
contrast   | int    |   32768 |   32768 | range is 0 => 65535
color      | int    |   32768 |   32768 | range is 0 => 65535
hue        | int    |   32768 |   32768 | range is 0 => 65535
Balance    | int    |       0 |   32768 | range is 0 => 65535
Bass       | int    |       0 |   32768 | range is 0 => 65535
Treble     | int    |       0 |   32768 | range is 0 => 65535
mute       | bool   | off     | off     |
chroma agc | bool   | off     | off     |
combfilter | bool   | off     | off     |
automute   | bool   | on      | off     |
luma decim | bool   | off     | off     |
agc crush  | bool   | on      | off     |
vcr hack   | bool   | off     | off     |
whitecrush | int    |     207 |     207 | range is 0 => 255
whitecrush | int    |     127 |     127 | range is 0 => 255
uv ratio   | int    |      50 |      50 | range is 0 => 100
full luma  | bool   | off     | off     |
coring     | int    |       0 |       0 | range is 0 => 3
```Is there a problem with the tuner being mis-identified or something? I grabbed tvtime and ran tvtime-scanner and it was able to detect channels. Here's the dmesg output for bttv on the first card (video0/vbi0):
```
[42457.057485] bttv: driver version 0.9.18 loaded
[42457.057489] bttv: using 8 buffers with 2080k (520 pages) each for capture
[42457.057953] bttv: Bt8xx card found (0).
[42457.057969] bttv0: Bt878 (rev 17) at 0000:01:07.0, irq: 17, latency: 32, mmio: 0xfeaff000
[42457.057998] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[42457.058001] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[42457.058032] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[42457.060518] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[42457.090432] bttv0: Hauppauge eeprom indicates model#44801
[42457.090434] bttv0: tuner type=2
[42457.100171] bttv0: audio absent, no audio device found!
[42457.107211] bttv0: registered device video0
[42457.107426] bttv0: registered device vbi0
[42457.107442] bttv0: PLL: 28636363 => 35468950 .
[42457.108673] bttv0: PLL: 28636363 => 35468950 .
[42457.111307] bttv0: PLL: 28636363 => 35468950 . ok
```

I'm not sure what else to check. Video capture doesn't work with mencoder:
mencoder tv:// -tv driver=v4l2:device=/dev/video0:noaudio -ovc lavc -o foo.avi

and zvbi-ntsc-cc won't start. Any ideas?

---

### Post by ian_d on 2011-01-10
*bump*

Or is this something more appropriate for the linux-media mailing list? I don't know if it's a driver issue or what.

---

### Post by dlinear on 2011-01-11
Hi, Believe it or not, I had almost the exact same problem, although with newer kernels (IE, I had no problems with Ubuntu 06 or 07, but after 08...). I solved it by using tvtime with the following command. 

tvtime --input=1 -d /dev/vbi0 --inputwidth=640
# for some reason you need to point the dev to the vbi device if you want closed captions to work!?!? WTF

I always had used tvtime prior to this, but the key was telling tvtime to use this device. 

I hope this helps.

Oh I forgot to mention that I start zvbi-ntsc-cc with -d /dev/vbi0 too.

---

