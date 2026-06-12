---
title: "Sound in Ubuntu, but not Lubuntu (PCM missing in alsamixer)"
date: 2012-07-23
forum: Multimedia Software
---

### Post by efflandt on 2012-07-23
I was doing a side by side comparison of 64-bit 12.04 Ubuntu and Lubuntu on a tablet PC (Acer W500P) and they both installed and boot fine from SD card slot with a common /home partition.  In Ubuntu sound works fine without doing anything.  In Lubuntu there is no volume control, no sound, and alsamixer shows no PCM even though both appear to have the same sound modules installed.

[B]So what does Ubuntu do differently with alsa by default than Lubuntu does, and what should I look for to get PCM to show up and sound working in Lubuntu?
[/B] 
Other points of reference:

Does the same from live/install system booted from USB memory stick on same tablet PC (no sound in Lubuntu).

On older laptop (2006) same USB live/install with only single analog sound device shows a volume control, but the icon appears muted (double dash) and whether mute is checked or unchecked volume remains at minimum and cannot be moved.  Master in alsamixer follows check or uncheck of mute in the applet, but there is no PCM.  Sound works fine in 64-bit Ubuntu 12.04 on that laptop.

Only on my desktop (in sig) does Lubuntu live/install USB show a proper unmuted volume icon, PCM shows up in alsamixer, and sound works.  It has both nvidia HDMI and analog audio, but I am just using analog stereo.

With Lubuntu booted on tablet PC (and alsamixer in Ubuntu at bottom):

```
LUBUNTU 12.04

uname -a
Linux LUBUNTU-1204 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

efflandt@LUBUNTU-1204:~$ cd /usr/share/sounds/alsa
efflandt@LUBUNTU-1204:/usr/share/sounds/alsa$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

efflandt@LUBUNTU-1204:/usr/share/sounds/alsa$ aplay Front_Center.wav
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:682: audio open error: No such file or directory

From: sudo lspci -v

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
    Subsystem: Acer Incorporated [ALI] Device 0577
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at 90144000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 0577
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at 90140000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

alsamixer:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.25 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HD-Audio Generic                               F1:  Help               &#9474;
&#9474; Chip: ATI R6xx HDMI                                  F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                  < S/PDIF >                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.25 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                     F1:  Help               &#9474;
&#9474; Chip: Realtek ALC269VB                               F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -6.75]                        Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                    &#9474;
&#9474;      &#9474;  &#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;  &#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;  &#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;
&#9474;      &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9492;&#9472;&#9472;&#9496;        &#9500;&#9472;&#9472;&#9508;       Enabled      &#9474;
&#9474;      &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;                    &#9474;MM&#9474;                    &#9474;
&#9474;      &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;                    &#9492;&#9472;&#9472;&#9496;                    &#9474;
&#9474;       75       100<>100    100<>100      0<>0        0<>0                    &#9474;
&#9474;  <  Master   > Headphone    Speaker    Mic Boost     Beep     Auto-Mute M    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


UBUNTU 12.04

uname -a
Linux UBUNTU-1204 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

alsamixer (HD-Audio Generic is the same). Note that Ubuntu shows PCM:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.25 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                     F1:  Help               &#9474;
&#9474; Chip: Realtek ALC269VB                               F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -6.75]                        Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;               &#9474;
&#9474;    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;               &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;       &#9500;&#9472;&#9472;&#9508;       &#9500;&#9472;&#9472;&#9508;       &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;     Enabled   &#9474;
&#9474;    &#9474;OO&#9474;       &#9474;OO&#9474;       &#9474;OO&#9474;                             &#9474;MM&#9474;               &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;                             &#9492;&#9472;&#9472;&#9496;               &#9474;
&#9474;     75      100<>100   100<>100   100<>100     0<>0       0<>0               &#9474;
&#9474;<  Master  >Headphone   Speaker      PCM     Mic Boost     Beep    Auto-Mute  &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```lsmod in Lubuntu:

```
Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
fglrx                3263886  99 
arc4                   12529  2 
ath9k                 132390  0 
mac80211              506816  1 ath9k
sp5100_tco             13791  0 
i2c_piix4              13301  0 
acer_wmi               28418  0 
asix                   26919  0 
usbnet                 26212  1 asix
sparse_keymap          13890  1 acer_wmi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_hda_codec_realtek   223867  1 
btusb                  18288  1 
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
hid_multitouch         13003  0 
joydev                 17693  0 
k10temp                13166  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bluetooth             180104  13 rfcomm,bnep,btusb
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 acer_wmi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  3 ath9k,mac80211,ath
snd                    78855  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ext2                   73795  3 
usbhid                 47199  1 hid_multitouch
hid                    99559  2 hid_multitouch,usbhid
ums_realtek            18248  0 
uas                    18180  0 
usb_storage            49198  4 ums_realtek
```

---

### Post by ajgreeny on 2012-07-23
I have no idea if this will help or not, but I had some sound problems on an old laptop that I use with Lubuntu 12.04.  Many played back sounds of, for example, recordings with audacity, or sound-recorder, played at slow speed.  I had previously used this same laptop to record using Ubuntu 10.04 with no problems of any sort, so I knew it was possible, I just didn't know why it did not work with Lubuntu 12.04.

The only obvious difference I could think of was the lack of pulseaudio in Lubuntu, so I installed it, along with the dependencies, including pavucontrol (pulseaudio volume control).

BINGO!  It worked and suddenly sound was working exactly as it should.  I am aware that some users dislike pulseaudio and even remove it from Ubuntu, but I have never had any problems with it and like it as it gives simultaneous-output sound, ie from two or more sound applications running together.

Give it a try; it may work for you too.  If it is not a solution, or adds to your problems, remove it again.  Synaptic keeps a good record of exactly what is installed in its history dialog, so use that to make life easy; it comes as default in Lubuntu 12.04.

---

### Post by efflandt on 2012-07-23
Installing **pulseaudio** and **pavucontrol** seemed to resolve missing sound in Lubuntu.  A working volume control appeared in bottom panel after rebooting, alsamixer shows PCM, and sound works.  I thought pulseaudio was just a front end for alsa, but apparently helps make it work.

It is just strange that Lubuntu does not have reliable working sound by default, and nothing in their FAQ's that I found about how to fix that.

---

