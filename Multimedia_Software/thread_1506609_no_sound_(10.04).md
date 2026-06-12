---
title: "no sound (10.04)"
date: 2010-06-10
forum: Multimedia Software
---

### Post by yaxoft on 2010-06-10
Hi.

I've installed Ubuntu 10.04 (dual boot with Windows XP SP3).
I have no sound in ubuntu (windows plays sound OK), from any application (even not the login screen).

I read [SoundTroubleshooting article]("https://help.ubuntu.com/community/SoundTroubleshooting"), but everything there is OK.

Ubuntu recognize my card, but no sound is heard.

kernel version: 2.6.32-22
```
user@lnx:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,user


user@lnx:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


user@lnx:~$ find /lib/modules/`uname -r` | grep snd | wc -l
217


user@lnx:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7267
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cfe3c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...

```

[LIST]
[*]alsamixer command does recognize my card.
[*]my card is not muted (In System > Preferences > Sound).
[*]my speakers and my headphones are connected properly (as I said, Windows does play music).
[*]I've tried to disconnect and reconnect the speakers, nothing changed.
[/LIST]

Thanks in advance.

---

### Post by lidex on 2010-06-13
Can you post the output of these terminal commands for me please:
```

dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by vasiauvi on 2010-06-23
Hello,
If @yaxoft did'nt responded I can respond in my place because I have the same problem:
- Ubuntu 10.04 kernel 2.6.32-23 generic
- I had sound but one day when the sound disappeared, not after restart or after upgrade but in the running time...
- gstreamer-properties and I hit test I have sound but I don't have sounf in other way...

```

dpkg -l | grep "alsa"
ii  alsa-base                                                1.0.22.1+dfsg-0ubuntu3                                  ALSA driver configuration files
ii  alsa-oss                                                 1.0.17-3                                                ALSA wrapper for OSS applications
ii  alsa-utils                                               1.0.22-0ubuntu5                                         ALSA utilities
ii  alsamixergui                                             0.9.0rc2-1-9                                            graphical soundcard mixer for ALSA soundcard
ii  alsaplayer-alsa                                          0.99.80-5                                               PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                                        0.99.80-5                                               PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                                           0.99.80-5                                               PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                                               4.60-0ubuntu8                                           Bluetooth audio support
ii  gnome-alsamixer                                          0.9.7~cvs.20060916.ds.1-2                               ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                       0.10.28-1                                               GStreamer plugin for ALSA
ii  libesd-alsa0                                             0.2.41-6ubuntu1                                         Enlightened Sound Daemon (ALSA) - transition
ii  linux-backports-modules-alsa-2.6.32-23-generic           2.6.32-23.16                                            Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic               2.6.32.23.24                                            Backported drivers for alsa-driver snapshot.
ii  python-alsaaudio       

```
 and
```

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC660-VD

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054

```

```
fgrep -ie 'audio' /etc/group
audio:x:29:pulse

```

```
sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/vasia not ours.
card 0: SB [HDA ATI SB], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Can anyone help me???
Thanks!

---

### Post by lidex on 2010-06-25
*vasiauvi*:
You may have the same problem, but different hardware, so likely a different fix.
Note this:
```
Home directory /home/vasia not ours.

```

Check the permissions on your home folder.

---

