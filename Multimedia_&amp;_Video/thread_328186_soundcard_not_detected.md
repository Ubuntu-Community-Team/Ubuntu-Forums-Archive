---
title: "soundcard not detected"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by lanquarden on 2006-12-30
Hello,

about a year ago I installed ubuntu 5.10 on the computer at home (sound was working without additional configuration), recently I reinstalled ubuntu 5.10 but the soundcard didn't seem to be detected any more. So I decided to update to ubuntu 6.06, that didn't make any difference.

The strange thing is that when GDM loads, I hear a sound coming out of the boxes, once Gnome starts to load nothing any more.

The soundcard is an onboard one, the specs of it can be found [here]("http://www.gigabyte.eu/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=1335&ProductName=GA-8SIML").

If I want to start alsamixer it gives me following error: "alsamixer: function snd_ctl_open failed for default: No such device"

In **System > Preferences > Sound** I can't set the default soundcard, empty list.

I found the [Comprehensive Sound Problem Solution Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), tried reinstalling linux-sound-base, alsa-base and alsa-utils, it didn't make any difference. (Didn't try to compile from source though)

the output of lspci:
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
```

lsmod | grep snd:
```
snd_intel8x0           33692  0
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_rawmidi            25504  1 snd_mpu401_uart
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_seq_device          8716  1 snd_rawmidi
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_timer,snd_seq_device
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
```

 I don't what the problem may be ...

---

