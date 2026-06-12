---
title: "No sound coming out of speakers"
date: 2014-06-16
forum: Multimedia Software
---

### Post by bhlee on 2014-06-16
I am using ubuntu 14.04 LTS. No sound is coming out of my speakers, which are Sony VAIO VGP-SP3 I tried following most of the "Basic Troubleshooting Steps" in this document: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). The following is the output of "sudo aplay -l":

```

bhlee@bhleealuubuntu:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The following is the output of 'lspci -v | grep -A7 -i "audio"':

```

bhlee@bhleealuubuntu:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 0278
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV620 HDMI Audio [Radeon HD 3400 Series]
    Subsystem: Dell Device aa28
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

```

Any suggestions? Many thanks.

---

### Post by Yellow Pasque on 2014-06-16
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bhlee on 2014-06-17
[http://www.alsa-project.org/db/?f=042d0cbb4d67715532d4eaa70e3005799179ff25](http://www.alsa-project.org/db/?f=042d0cbb4d67715532d4eaa70e3005799179ff25)

---

### Post by Yellow Pasque on 2014-06-18
Is it possible you need to turn the volume up? Other than that, I don't see anything obviously wrong (though I don't claim to be an expert).
```
alsamixer
```

```
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
```

---

### Post by bhlee on 2014-06-23
No, I checked "alsamixer" in Terminal, and all of the relevant volume bars are turned up high enough.

---

### Post by soodvarun78 on 2014-06-23
You have USB Audio device for capture other than PCI devices. just plug  out USB and try, if not already done.

---

### Post by bhlee on 2014-07-01
Now, after unplugging the USB devices, I just have the following:

```

!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 44
 3 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdcfc000 irq 46

```

However, I still do not get any sound.

---

### Post by Yellow Pasque on 2014-07-01
Try latest kernel module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
(Make sure you have dkms package installed).

If that doesn't work, file a bug.
```
ubuntu-bug audio
```

---

### Post by lidex on 2014-07-01
Audio channels can be muted even with the volume set above zero. Make sure you don't see MM
at the bottom of the volume bars. If you do, select and hit the <M> key

---

### Post by bhlee on 2014-07-02
> **lidex said:**
> Audio channels can be muted even with the volume set above zero. Make sure you don't see MM
at the bottom of the volume bars. If you do, select and hit the <M> key

Yes, I checked this with "alsamixer" in Terminal. Yet, I still get no sound.

---

### Post by bhlee on 2014-07-02
Great news! I found out that all of my audio output was indeed muted. I checked "alsamixer" in Terminal, switched to "All" View, noticed "Auto-Mut" was Enabled and switched "Auto-Mut" to Disabled. I found this out after [reporting]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1336625") my issue as a bug, which is not really a bug. Please refer to this [bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1197290"), which investigates why "Auto-Mut" is Enabled, by default, beginning with kernel 3.10. Sound comes out from my speakers, now. Thank you for you help.

---

### Post by Yellow Pasque on 2014-07-02
Just remember that workaround if you plug headphones in and actually want the speakers to mute.
Please mark thread solved.

---

### Post by cb41 on 2014-07-02
are you bual booting from windows 8?

---

