---
title: "usb audio doesnt work anymore"
date: 2012-09-11
forum: Multimedia Software
---

### Post by Chiel92 on 2012-09-11
Hi,

I've got a fasttrack pro usb sound card, which used to work fine. However, last week suddenly no sound comes through it anymore on ubuntu. On windows it works however, so the soundcard isnt broken. On my parallel ubuntu studio installation it works only through jack. Why doesn't it play regularly through alsa, like it used to do?

The soundcard gets recognized fine and is selected as default.
Here is some info.
```
$ cat /proc/asound/modules 
 0 snd_usb_audio
 1 snd_hda_intel
 2 snd_hda_intel
``````

$ cat /proc/asound/cards
 0 [Pro            ]: USB-Audio - FastTrack Pro
                      M-Audio FastTrack Pro at usb-0000:00:1a.1-2, full speed
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf1500000 irq 45
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf1000000 irq 16
```Any help is very welcome! I really want my sound back in ubuntu!

---

### Post by marinara on 2012-09-13
.asoundrc file missing? check the audio troubleshooting page on the wiki

---

### Post by Chiel92 on 2012-09-20
> **marinara said:**
> .asoundrc file missing? check the audio troubleshooting page on the wiki

Thanks for your reply. An .asounrc file shouldn't be necessary for alsa to work, according to the documentation. 
(Just to mention: I can get sound through my onboard soundcard, but that's not what I want, obviously.)

I just followed the troubleshooting page here [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).
I think the following output might be of interest.

This command lists the usb sound card.
```
$ sudo aplay -l
[sudo] password for chiel: 
**** List of PLAYBACK Hardware Devices ****
card 0: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```This one doesn't though.
```
$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0219
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f1500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0219
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f1000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```Does this mean something?


ps. I do not have a lubuntu install as the prefix suggests, but a regular ubuntu 12.04. Just clicked the wrong entry.

---

### Post by Chiel92 on 2012-09-24
Bump.

A bit more info.
In "System Settings"->"Sound"->"Output" the usb-soundcard is also visible. However, when I click it to select, the sound disappears. When I select the built-in-soundcard again the sound reappears. So I think the usb-soundcard is definitely recognized correctly, but somehow there are problems sending audio through it.

As I'm not aware to have changed anything causing my sound to break, could there have been some (alsa-)update breaking it?

---

### Post by Scott Goodgame on 2012-09-24
Did you try looking at alsamixer from the command prompt?
F6 select your sound card and make sure it isn't muted... Had a similar problem with my $2 usb sound once

---

### Post by Chiel92 on 2012-09-25
> **Scott Goodgame said:**
> Did you try looking at alsamixer from the command prompt?
F6 select your sound card and make sure it isn't muted... Had a similar problem with my $2 usb sound once

Thanks for your reply. I indeed did that. At startup, alsamixer shows my usb sound card and informs that it doesnt have any controls. So I can't mute or unmute it. (This was also the case when the card worked.) When I press F6 I can choose between the usb soundcard (which is at place 0) and two other internal cards.  But since the usbsoundcard was already selected, I do not change the selection.

---

### Post by BicyclerBoy on 2012-09-25
check that aplay -l works without sudo..You should not need to use sudo.

A USB soundcard will not show under hwpci...try:
lsusb
lsmod
(need to search for approp driver)

speaker-test -l 1 -c 2 -r 48000 -D hw:0,0

Try the pulse-audio config tool pavucontrol..

---

### Post by Chiel92 on 2012-09-25
aplay -l also works without sudo indeed.

Here is the output of the commands you suggested.
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 004 Device 002: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 005 Device 002: ID 046d:c31b Logitech, Inc. Compact Keyboard K300
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
``````

$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13516  1 
snd_hda_codec_hdmi     31775  4 
snd_hda_codec_conexant    52554  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_usb_audio         101566  0 
nvidia              10971098  43 
btusb                  17912  0 
bluetooth             158438  11 rfcomm,bnep,btusb
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_device         14172  3 snd_seq_midi,snd_seq,snd_rawmidi
iwlwifi               366425  0 
videodev               86588  1 uvcvideo
mac80211              436455  1 iwlwifi
snd                    62064  22 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
acer_wmi               23612  0 
soundcore              14635  1 snd
sparse_keymap          13658  1 acer_wmi
cfg80211              178679  2 iwlwifi,mac80211
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
joydev                 17393  0 
psmouse                86421  0 
serio_raw              13027  0 
video                  19068  0 
wmi                    18744  1 acer_wmi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
tg3                   141369  0 

```It seems to me that the output is fine so far.

When running ```
speaker-test -l 1 -c 2 -r 48000 -D hw:0,0
``` I get noise out of the speakers!

UPDATE: I played a bit around with pavucontrol, and I get sound now!!!
After reboot, the sound is still there, without having to start pavucontrol.
So I think it was indeed muted somehow, while the tools I had installed weren't able to unmute it.
Thanks for your help!
Thread marked as solved.

---

