---
title: "Pinnacle 800e dtv tuner, /dev/dvb/* missing"
date: 2010-10-04
forum: Multimedia Software
---

### Post by efflandt on 2010-10-04
I am trying to get a Pinnacle 800e USB ATSC digital TV tuner working in 64-bit Lucid.  I followed the 800e wiki for extracting the firmware file that needs to be in /lib/firmware, so dmesg output recognizes it without errors just like shown in the wiki.  No idea what modules it should use, but seem to be loaded:

```
Module                  Size  Used by
lgdt330x                9070  0 
em28xx_dvb              9311  0 
dvb_core              103025  2 lgdt330x,em28xx_dvb
em28xx_alsa             7398  1 
tuner_xc2028           20800  1 
tuner                  23256  1 
tvp5150                16347  1 
em28xx                 96207  2 em28xx_dvb,em28xx_alsa
v4l2_common            18357  3 tuner,tvp5150,em28xx
videodev               40518  4 tuner,tvp5150,em28xx,v4l2_common
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    11956  1 videodev
ir_common              43415  1 em28xx
videobuf_vmalloc        6635  1 em28xx
videobuf_core          19301  2 em28xx,videobuf_vmalloc
tveeprom               13882  1 em28xx
```udev generated listings for it in /dev/v4l

**ls /dev/v4l/by-id**
usb-Pinnacle_Systems_PCTV_800e_070101022882-video-index0
**ls /dev/v4l/by-path**
pci-0000:00:02.2-usb-0:1:1.0-video-index0  pci-0000:00:02.2-usb-0:1:1.0-video-index1

I can scan for ATSC channels with w_scan to create channels.conf with valid channels for my area (Chicago), so antenna is good and it is sort of working up to that point.

But nothing created /dev/dvb/ or anything beyond that, so tests using dvb-apps or dvbsnoop do not work.  For example with ~/.azap/channels.conf:

**azap -r wls-dt**
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: error while parsing modulation (syntax error)
[probably because /dev/dvb does not exist rather than channels.conf issue]

**dvbscan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB**
Failed to open frontend
[probably also because /dev/dvb/adapter0/frontend0 does not exist]

So what is supposed to create /dev/dvb/ and missing hooks in it?

---

### Post by efflandt on 2010-10-16
That was in Lucid.  Nobody knows what should create /dev/dvb/ and things under it?

---

### Post by efflandt on 2010-10-17
While trying this on another computer, I discovered that /dev/dvb/ was created when booting with the USB tuner already connected, and I am a member of group **video**.

**ls -l /dev/dvb/adapter0**
total 0
crw-rw----+ 1 root video 212, 1 2010-10-16 22:00 demux0
crw-rw----+ 1 root video 212, 2 2010-10-16 22:00 dvr0
crw-rw----+ 1 root video 212, 0 2010-10-16 22:00 frontend0
crw-rw----+ 1 root video 212, 3 2010-10-16 22:00 net0

w_scan was able to find local channels with names on either computer, so that part works in 32 or 64-bit Lucid. But **dvbsnoop -s pidscan** comes up empty and  dvbscan does not work:

**dvbscan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB** 
Unable to query frontend status

And when trying to azap the following channels.conf entry (or any other) it fails:
THIS Chicago:551000000:VSB_8:97:100:6

**azap -r "this chicago"**
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: error while parsing modulation (syntax error)

So everything appears to be in place, but none of the dvb tools work, other than w_scan being able to find valid channels for  ~/channels.conf and ~/.azap/channels.conf:

```
WLS-DT:177000000:VSB_8:49:52:1
Livwell:177000000:VSB_8:65:68:2
WLS-SD:177000000:VSB_8:81:84:3
WGN-DT:503000000:VSB_8:49:52:3
service_id 4:503000000:VSB_8:65:68:4
WCIU-DT Chicago:551000000:VSB_8:49:52:3
WWME-CA Chicago:551000000:VSB_8:65:68:4
WMEU-CA Chicago:551000000:VSB_8:81:84:5
THIS Chicago:551000000:VSB_8:97:100:6
Chicago Ethnic Television:551000000:VSB_8:129:132:8
WWME-CA Chicago:551000000:VSB_8:65:68:9
WMEU-CA Chicago:551000000:VSB_8:81:84:16
NBC5   :563000000:VSB_8:81:84:5
NBC5-WX:563000000:VSB_8:97:100:6
NBC5-US:563000000:VSB_8:113:116:7
WFLD   :575000000:VSB_8:49:52:3
WJYS Digital - Your station for inspiration.:605000000:VSB_8:49:51:1
My Christian TV:605000000:VSB_8:65:67:2
WJYS2:605000000:VSB_8:97:99:4
Univision Chicago:617000000:VSB_8:49:52:1
WLS-DT:653000000:VSB_8:49:52:1
Livwell:653000000:VSB_8:65:68:2
WLS-SD:653000000:VSB_8:81:84:3
WSNS HD:659000000:VSB_8:49:52:3
Inmigrante TV
WSNS-TV
454 N. Columbus Drive
Chicago, IL 60611
312-836-5555:659000000:VSB_8:65:68:4
WTTW-HD:671000000:VSB_8:49:52:3
WTTW-DT:671000000:VSB_8:65:68:4
WTTW-DT:671000000:VSB_8:81:84:5
WTTW-DT:671000000:VSB_8:97:100:6
WXFT-HD Telefutura Chicago:689000000:VSB_8:49:52:1
WXFT-SD Telefutura Chicago:689000000:VSB_8:65:68:2
WPWR-TV:695000000:VSB_8:49:52:3
```

---

