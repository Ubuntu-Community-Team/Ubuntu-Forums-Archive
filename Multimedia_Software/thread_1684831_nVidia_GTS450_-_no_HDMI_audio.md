---
title: "nVidia GTS450 - no HDMI audio"
date: 2011-02-09
forum: Multimedia Software
---

### Post by moltek on 2011-02-09
Hello,
I have difficulty getting my GTS450 to transfer audio to AV receiver. I have installed the newest Nvidia driver 260.19.36, but there is still no soundcard visible "fully" (I get message in alsamixer: "This sound device does not have any controls.". I have switched off the onboard soundcard in BIOS.

Here is my [COLOR=Blue][output]("http://www.alsa-project.org/db/?f=a1cbc9132bca37d27dbdcd92916ffe03f5dbeff8")[/COLOR] of alsa-info script.

EDIT: I have upgraded kernel to 2.6.38-020638rc4 then NVIDIA driver to 260.19.36 again, then followed t[hese instructions]("http://ubuntuforums.org/showthread.php?t=1668737") and.... got the sound!!!!
For now it is only stereo though.

EDIT2: Only stereo works. Here is new alsa-info [output]("http://www.alsa-project.org/db/?f=67a29fd12cb21f2177a8b8a0aded83bb983755cf").
I have upgraded ALSA to the newest 1.0.24 but this solved nothing. Command:
```
speaker-test -twav -c8 -Dhdmi:NVidia
```gives:
```
speaker-test 1.0.24.2

Playback device is hdmi:NVidia
Stream parameters are 48000Hz, S16_LE, 8 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 16 to 4096
Period size range from 8 to 2048
Using max buffer size 4096
Periods = 4
was set period_size = 1024
was set buffer_size = 4096
 0 - Front Left
 4 - Centre
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE

```but sound is only produced for FL and FR.



I have read quite a lot of forum posts, faqs, howtos, etc. but most of the issues are only related to having no sound at all.

Please, any ideas?

---

### Post by moltek on 2011-02-26
Still nothing despite having the best and newest Nvidia driver, Alsa and kernel. Only stereo via HDMI works :(

I have just run aplay -L again getting this:
```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```
It seems that "hw" is the device I need to use. How can I use it instead of "hdmi" that now seems to be used?

---

### Post by moltek on 2011-03-01
I have just seen this b[ug report]("https://bugzilla.kernel.org/show_bug.cgi?id=28592"). It seems upgrade to 2.6.38 rc5 might solve the issue :)     


EDIT: It did not solve the issue. :(

---

### Post by moltek on 2011-03-11
Having no luck with Mint, I decided to start from fresh Maverick install (using USB disk). Here are the steps
- install Ubuntu 10.10 Desktop x86
- no sound, audio does not work (aplay -l does not show any NVidia devices),
- install 270.39 NVidia driver from *ppa:ubuntu-x-swat/x-updates*
- still no sound, aplay -l does not show any audio devices (my onboard audio is switched off),
- install alsa update from *ppa:ubuntu-audio-dev/ppa*
- aplay -l shows HDA Nvidia, sound is played by sound-test (but only 2 channels, rest of them are not audible).

ELD data is correct, showing possible 8 channels and all multichannel codecs.
```
monitor_present        1
eld_valid        1
monitor_name        DENON-AVAMP

connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0xee11
product_id        0x1d
port_id            0x20000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x5f] FL/FR LFE FC RL/RR RC RLC/RRC
sad_count        7
sad0_coding_type    [0x1] LPCM
sad0_channels        8
sad0_rates        [0x1ee0] 44100 48000 88200 176400 192000 384000
sad0_bits        [0xe0000] 16 20 24
sad1_coding_type    [0x7] DTS
sad1_channels        6
sad1_rates        [0x6c0] 48000 88200 176400 192000
sad1_max_bitrate    1536000
sad2_coding_type    [0x2] AC-3
sad2_channels        6
sad2_rates        [0xe0] 44100 48000 88200
sad2_max_bitrate    640000
sad3_coding_type    [0xb] DTS-HD
sad3_channels        8
sad3_rates        [0x1ec0] 48000 88200 176400 192000 384000
sad4_coding_type    [0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad4_channels        8
sad4_rates        [0xc0] 48000 88200
sad5_coding_type    [0xc] MLP (Dolby TrueHD)
sad5_channels        6
sad5_rates        [0x1ec0] 48000 88200 176400 192000 384000
sad6_coding_type    [0xc] MLP (Dolby TrueHD)
sad6_channels        8
sad6_rates        [0x6c0] 48000 88200 176400 192000

```Again, any comments on how to solve this? Should I simply wait for Natty and hope for the best?

---

### Post by negge on 2011-10-03
Did you ever solve this problem? 

I'm having the exact same problem with a Geforce 520. I'm still on Debian's 2.6.32-5 kernel (although with the newest ALSA to get the device to show up) so I thought the kernel bug you linked to (which sadly seems to have disappeared from the Internet now that kernel.org got hacked) would solve it, but I guess it didn't?

If anyone else has any useful information regarding this problem, please post.

**Edit: I solved it!**

The bug report you linked to is down but here's the patch attached to it: [https://github.com/mirrors/linux/commit/11839aed21881d7edd65dd79f22a8eb18426f672#sound/pci/hda/patch_hdmi.c]("https://github.com/mirrors/linux/commit/11839aed21881d7edd65dd79f22a8eb18426f672#sound/pci/hda/patch_hdmi.c")

As I had previously compiled alsa-drivers 1.0.24 I just applied that patch manually and recompiled, and woila, speaker-test -D default -c6 now outputs noise on all channels. This also meant that XBMC started playing 6-channel FLAC files out of the box (where previously I got only the front channels).

I hope this helps someone in the future!

---

### Post by moltek on 2011-10-04
Congrats! good job.

I was talking to myself in this thread and I forgot to put the solution in. I have solved it and posted a [complete story]("http://www.nvnews.net/vbulletin/showthread.php?t=160187") on NvNews forums.

---

